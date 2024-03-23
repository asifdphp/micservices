## How it works

For each microservice: docker images are downloaded, and containers are built [App, Queue, Database] from the DockerFile.
After that the docker compose file runs a few `[.sh]` files inside the container to prepare the microservice for work.

### `[start.sh]` file is responsible for:

1. Install dependencies.
2. Create `[.env]` file.
3. Run a command to initialize the laravel app:

    - Generate an app key.
    - Migrate the database.

    Admin-only commands:

    - Seed the database.
    - Install Laravel Passport.
    - Create a Passport client.
    - Create a sample user.
    - Create a token.
    - <a name="token"></a>Store the token in a file called `[/api_token.txt]` to use it later with Postman.
    - Serve the Laravel app.



    ## Usage

-   Make sure Docker is running.
-   Populate `[.env.example]` with your RabbitMQ account details.

    ```
    RABBITMQ_HOST=
    RABBITMQ_USER=
    RABBITMQ_PASSWORD=
    RABBITMQ_VHOST=
    ```

-   Mainone microservice.

    ```
    $ cd micservices/mainone
    $ docker compose up -d
    ```

-   Maintwo microservice.

    ```
    $ cd micservices/maintwo
    $ docker compose up -d
    ```