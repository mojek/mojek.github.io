---
layout: default
title: Django workflow
categories: [django, best practice]
---

1. Make project directory and enter

    ```shell
    mkdir <project_folder> && cd <project_folder>
    ```

2. Install Django with pipenv

    ```shell
    pipenv install django==2.2.6
    ```

3. Install postgresql lib

    ```shell
    pipenv install psycopg2-binary==2.8.3
    ```

4. Create django project

    ```shell
    django-admin startproject <project_name> .
    ```

5. Create Dockerfile and docker-compose.yml

   ```shell
    touch Dockerfile
    touch docker-compose.yml
   ```

   ```dockerfile
    # Pull base image
    FROM python:3.7-slim

    # Set environment varibles
    ENV PYTHONDONTWRITEBYTECODE 1
    ENV PYTHONUNBUFFERED 1

    # Set work directory
    WORKDIR /code

    # Install dependencies
    COPY Pipfile Pipfile.lock /code/
    RUN pip install pipenv && pipenv install --system

    # create user
    RUN useradd -ms /bin/bash newuser
    USER newuser

    # Copy project
    COPY . /code/
   ```

   ```yml
    # docker-compose.yml
    version: '3.7'

    services:
    web:
        build: .
        command: python /code/manage.py runserver 0.0.0.0:8000
        volumes:
        - .:/code
        ports:
        - 8000:8000
        depends_on:
        - db  
        environment:
        - SECRET_KEY=hn_3!__*m$$am9+mk=$$9s8$$@mp)^3-=i)c6_1w2o67%ch%6$$h0c
        - DEBUG=1
        - DB_HOST=db
        - DB_NAME=<project_name>
        - DB_USER=postgres_user
        - DB_PASS=supersecret
    db:
        image: postgres:11
        environment:
         - POSTGRES_DB=<project_name>
         - POSTGRES_USER=postgres_user
         - POSTGRES_PASSWORD=supersecret
        volumes:
        - postgres_data:/var/lib/postgresql/data/
    volumes:
        postgres_data:
   ```

6. Creating Tests for custom users

    ```python
    from django.test import TestCase
    from django.contrib.auth import get_user_model

    from core import models


    def sample_user(email="test@mojek.pl", password="testpass"):
        """Create sample user"""
        return get_user_model().objects.create_user(email, password)


    class ModelTests(TestCase):
        def test_create_user_with_email_successful(self):
            """Test creating new user with email is ok"""
            email = "test@mojek.pl"
            password = "Testpass123"
            user = get_user_model().objects.create_user(
                email=email, password=password
            )
            self.assertEqual(user.email, email)
            self.assertTrue(user.check_password(password))

        def test_new_user_email_normalized(self):
            """Test the email for a new user is normalized"""
            email = "mojek@MOJEK.pl"
            user = get_user_model().objects.create_user(email, "test123")
            self.assertEqual(user.email, email.lower())

        def test_new_user_invalid_email(self):
            """Test creating user with no email raises error"""
            with self.assertRaises(ValueError):
                get_user_model().objects.create_user(None, "test123")

        def test_create_new_superuser(self):
            """Test creating a new superuser"""
            user = get_user_model().objects.create_superuser(
                "test@mojek.pl", "test123"
            )
            self.assertTrue(user.is_superuser)
            self.assertTrue(user.is_staff)
    ```        

7. Creating Custom User Model 

    ```python
        # users/models.py 
        from django.db import models
        from django.contrib.auth.models import (
            AbstractBaseUser,
            BaseUserManager,
            PermissionsMixin,
        )
        from django.conf import settings


        class UserManager(BaseUserManager):
            def create_user(self, email, password=None, **extra_fields):
                """Creates and saves new User"""
                if not email:
                    raise ValueError("Users must have an email")
                user = self.model(email=self.normalize_email(email), **extra_fields)
                user.set_password(password)
                user.save(using=self._db)
                return user

            def create_superuser(self, email, password):
                """Create and save new super user"""
                user = self.create_user(email, password)
                user.is_staff = True
                user.is_superuser = True
                user.save(using=self._db)

                return user


        class User(AbstractBaseUser, PermissionsMixin):
            """Custom user model that suports using email instead username"""

            email = models.EmailField(max_length=255, unique=True)
            name = models.CharField(max_length=255)
            is_active = models.BooleanField(default=True)
            is_staff = models.BooleanField(default=False)

            objects = UserManager()

            USERNAME_FIELD = "email"

    ```

 ```python
    # bookstore_project/settings.py 
    INSTALLED_APPS = [ 
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # Local
    'users.apps.UsersConfig' , # new 
    ]

    AUTH_USER_MODEL = 'users.CustomUser' # new
 ```