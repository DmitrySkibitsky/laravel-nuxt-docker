# About (Currently work in progress)
Dockerized started template for Laravel + Nuxt.JS easy development.

# Installation
// todo

# Usage
// todo

## Available containers
* Nginx (as proxy resolver between Laravel and Nuxt)
* PHP-FPM version 7.3
* Node version 12.4 (For SSR)
* Redis
* PostgreSQL version 11.3
* NODE-CLI for front-end workspace
* PHP-CLI for back-end workspace

### TODO LIST:
- add instructions about reinstallation nuxt and laravel with fresh versions
- install eslinter
- add IDE settings instructions (optional)
- add logs to .gitignore
- add docker ignore
- add other containers (selenium, echo-server, queue, schedule)
- migrate to SSL and probably HTTP2
- add instructions about axios usage
- proxy redis port (for gui tools access)
- add commands for postgres usage
- add commands for displaying logs
- add commands for clearing logs
- add logs directory and store all logs inside of it

**If you want, you can reinstall fresh laravel version with the following commands:**

Remove old laravel directory
```
sudo rm -rf api
```

Create new empty directory (name must be 'api' because it mounts inside docker-containers)
```
mkdir api
```

Restart docker containers to allow to remount the new 'app' directory
```
docker-compose down
docker-compose up -d
```

Install laravel inside container working directory (our just created api directory in the step above)
```
docker-compose exec php-cli composer create-project --prefer-dist laravel/laravel .
```

Give permissions for all generated from docker files and directories to current user
```
sudo chown ${USER}:${USER} -R api
```

Set up laravel permissions
```
sudo chmod -R 777 api/bootstrap/cache
sudo chmod -R 777 api/storage
```

Open http://localhost:8081 and make sure it works

**If you want, you can reinstall fresh laravel version with the following commands:**

```
yarn create nuxt-app client
```

Restart node container for executing fresh nuxt build process
```
docker-compose restart node
```
