# minify-laravel-docker-compose
A very very simple Docker Compose that setup 4 container (mariadb - laravel - redis - phpmyadmin) for local Laravel development.
This Docker-Compose is suitable for development NOT production!

> I Prefer Laravel Sail for Docker development environment. read document [here](https://laravel.com/docs/8.x/sail).

## Usage

To get started, install Docker [here](https://docs.docker.com/docker-for-mac/install/).

Next, clone this repository.

Open `.env` file in your editor. These are the default values, but you can change them.
```dotenv
APP_NAME=laravel
APP_PORT=8080
DB_PORT=33060
PHPMYADMIN_PORT=8081
```
- APP_NAME is your project name.
- APP_PORT is your local port to connect to the laravel app.
- DB_PORT is your local port to connect to the Mariadb.
- PHPMYADMIN_PORT is your local port to connect to the phpmyadmin.

Finally, run this command at the root of the folders.
```
$ docker-compose up -d 
```

Now, your containers are up! now you can copy your laravel files into laravel directory OR create new laravel project with composer in laravel directory.

you can access to laravel project with 8080 port. (if you didn't change APP_PORT in `.env` file!)
```dotenv
localhost:8080
```
and phpmyadmin access in:
```dotenv
localhost:8081
```

## Persistent MySQL/REDIS Storage
By default, all your data remains in the data directory! If you want to delete data only empty data folder.