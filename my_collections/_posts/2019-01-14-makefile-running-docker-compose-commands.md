---
layout: post
title: Makefile running docker-compose commands
categories: [docker, linux]
---

Running docker-compose commands and remembering them is quite annoying.
To speed up the work, create a Makefile file in the main directory.
Makefile should be used not only in this case, but also for other complex commands.
This is an example for a container in which Django is running.

```bash
$ make run
$ make build
$ make test
$ make flake8
```

```makefile
PROJECT_DIR_NAME:=management_django_service
ENTER_DJANGO:=docker-compose exec djangoweb
DJANGO_USER_UID:=$(shell id -u)
build:
    ## build necessary stuff for our project to run (docker images)
    docker-compose build

run:
    ## start containers with docker-compose and attach to logs
    docker-compose up --no-build

rund: 
    ## start containers with docker-compose (detached mode)
    docker-compose up --no-build -d

stop:
    ## stop all running containers for this project
    docker-compose stop

enter:
    ## enter the Django container 
    ## (want to play freely with manage.py commands? 
    ## just `make enter` and have fun)
    $(ENTER_DJANGO) sh

test:
    $(ENTER_DJANGO) sh -c "python manage.py test && flake8"

flake:
    $(ENTER_DJANGO) flake8






```

