# seed-keycloak-golang

This seed it's about how to implement a keycloak(kk) authentication using docker-compose and golang to provide a simple way to call the kk API. We will understand how Openid protocol works with kk, how to select other themes, etc.

## What you need?

* Docker installed
* Docker-compose installed
* Golang installed

## Init Project

Run in terminal `docker-compose up --build` to download and build the images inside Dockerfile and docker-compose file, maybe you need to run it with `sudo`.

## Dockerfile

This file contains the keycloak image that we will use.

## Docker-compose file

This file contains the kk service builded from Dockerfile and a mysql service, you will find the user and password inside docker-compose file.
