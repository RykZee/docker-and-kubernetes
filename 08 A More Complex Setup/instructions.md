# A More Complex project
Firstly create an empty src directory and run just the laravel with docker-compose using this command when standing in the root of the project:
`docker-compose run --rm composer create-project --prefer-dist laravel/laravel:^8.0 .`

This will generate a bunch of files. Open the .env file and change the DB_ variables to
```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=homestead
DB_USERNAME=homestead
DB_PASSWORD=secret
```

To run only the services needed and not the utility containers, you can use
`docker-compose up -d server php mysql`
It will start in detached mode and only start the services given. If you use the depends_on in the docker-compose.yaml file then you could simply specify server since it will depend on php and mysql.
You could also add `--build` to the command so it will always build.

`docker-compose up -d --build server`

For the artisan step, which populates DB and thus checks DB connection:
`docker-compose run --rm artisan migrate`
