# Docker Rails Starter

## Getting started
After cloning the repo, change all instances of `myapp` to the name of your app. Look in the following files:
- Dockerfile
- entrypoint.sh
- docker-compose.yml

Then run

```
docker-compose run web rails new . --force --no-deps --database=postgresql
```

Next, run

```
docker-compose build
```

Replace `config/database.yml` with the following content:

```
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password:
  pool: 5

development:
  <<: *default
  database: myapp_development


test:
  <<: *default
  database: myapp_test
  ```

Then boot the app up

```
docker-compose up
```

Create a database
```
docker-compose run web rails db:create
```

View your app at [http://localhost:3000](http://localhost:3000)

## Browser support config (optional)
After your Rails app is ready, you can optionally configure the list of browsers your app will support. You can do this by adding the following to your `.browserslistrc`

```
> 1%
last 2 versions
not ie <= 11
```
