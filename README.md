# Self-Hosted ChatBot With Docker Compose

## Introduction

Herzlich Willkommen, Welcome. Here you will learn, how to use a simple `docker compose` file to create a self-hosted ChatBot running a LLM of your choice on your own hardware without any data leaving your system.

To follow the Instructions, all you need is Docker and Docker Compose installed. If you do not have it installed yet, don't worry the official [Docker Docs](https://www.docker.com/) will help you set it up in a matter of minutes.

## Setup

### 1. Environment

Before running the script, you will need to configure some environment variables used for database authentication and pgAdmin. To help you with that, an `example.env` is provided. Copy this file and rename it to `.env`. You can set the variables to any value you wish. However, `pgAdmin` requires a correct syntax for the email (though, it may be a pseudo address).

### 2. Firing up the docker compose

To start the containers open up your preferred shell and navigate to the repository.

```
cd <path>/<to>/hsmz-sose25-disc-rdd/
```

#### 2. a

To start the docker compose, run the following command.

```sh
docker compose start
```

Do not worry, due to the size of the images, it may take a while at the first time.

You will see the containers logs right after they are started.

To end the application, press `<Ctrl-c>`.

#### 2. b

We can also start the containers detached from our session. Means, they will run in the background without occupying our shell session. To do so add the `-d` flag for "detach".

```sh
docker compose start -d
```

_When being finished with the application_, you can stop the containers, running the following command:

```sh
docker compose down
```

### 3. Open the application

After some minutes, the site should be up for the first time listening to the address `localhost:3000`.

### 4. Create Open WebUI login

When opened the first time, Open WebUI will ask you to create an account. As all chats, this account is only stored to your local database, so you are allowed to enter any login details. Just be clever enough to remember them :-).

### 5. Loading the first model

After logging in you will need to import an ollama LLM in order to start chatting.

So, navigate to `Profile` > `Settings` > `Administrator Settings` > `Models` and type in the name of the model you wish to use. Keep in mind its respective hardware requirements. A popular low-demand model would be `llama3`.

### 6. Start chatting

Chatting works just like any other chatbot you know. You should recognize that UI anyways :-).

## Inspect your database

As this is a demonstration project, I have included `pgAdmin` to inspect the shipped postgres database. To open pgAdmin visit `localhost:8080` and login with the credentials configured in `.env`.

Once logged in, you will need to configure a server. Therefore, hit "add new server" and name the connection the way you like. Unter "Connection" enter `postgres` as Host name and `5432` as port.

You should see the database now. Navigate to `configured database name` > `shemas` > `public` and you will see the tables created by Open WebUI. Using the `Query Tool` you may inspect them.
