# seed-keycloak-golang

This seed it's about how to implement a keycloak(kk) authentication using docker-compose and golang to provide a simple way to call the kk API. We will understand how Openid and OAuth 2 protocol works with kk, how to select other themes, etc.

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

## OAuth 2

Authorization flow elements.

* Resource Owner
* Client
* Resource Server
* Authorization Server

![Oauth 2 flow](https://user-images.githubusercontent.com/2284988/137121016-de010419-f7d2-4ade-9c48-a65afbff3078.png)

## Inside Admin

### Realms

Realm is a way to separate the context, by default we have the master realm, this realm has the objective to manage the keycloak.
To create a new realm, go to "add realm" below the master realm, give a name and that's it.

### Users

To add or manage a user go to "users". 

### Clients

when you have an app, and this app needs to make the authentication flow, then you will need a client. To manage the clients you will need to have a realm selected, go to "clients" option. A simple way to demonstrate de operation is create a new client,  let the openid-content selected and give a Root URL. This URL is a login url that your app will have. To show the flow we will use a SPA example came from keycloak "https://www.keycloak.org/app/".

Created the client, go to "https://www.keycloak.org/app/". There you will find the page asking you the Realm and the Client that you created before, save and will be redirect to Sign in.

Go ahead and make the login using the user created before.

## GoClient

Inside goClient path, you will see a small code written in goLang, this code will simulate the same flow on "clients" topic. To do it, change the "Access Type" inside your client to "Confidential" and get the secret in "credentials" tab. After it, you should change the root url, admin url and web Origins to "http://localhost:8081" because we will handle a server to do it, the valid redirect uris wil receive "http://localhost:8081*".

Execute in terminal the command "go mod init goclient". After it, you will find the files go.mod and go.sum in the source path. This files is marked like ignored inside .gitignore. To run the client, task "go run main.go".

### Flow request
1 - Task "http://loalhost:8081". Here you will be redirect to login page, hosted by keycloak. Make the login flow with your user and pass.
2 - The callback redirect will throw you to "/auth/callback" showing the access token.

### Access token

Get the access token and put inside "jwt.io", then you will see the decode access token like this.
![image](https://user-images.githubusercontent.com/2284988/138468675-a34b5ea7-66be-4166-9906-f2194a75d718.png)







