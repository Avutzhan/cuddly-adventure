```shell
docker-compose -f .docker/docker-compose.yml --project-directory .docker config
```

Note, that this command is run from ./docker-php-tutorial. If we would run this from ./docker-php-tutorial/.docker, we could simply use docker-compose config - but since we'll define that in a Makefile later anyway, the additional "verbosity" won't matter ;)

The actual build is triggered via
```shell
docker-compose -f .docker/docker-compose.yml --project-directory .docker build --parallel
```

To start the containers, we use
```shell
docker-compose -f .docker/docker-compose.yml --project-directory .docker up -d
```

Testing if everything works
```shell
sh .docker/docker-test.sh
```

Makefile as a central reference point

```shell
make docker-clean
make docker-init
make docker-build-from-scratch
make docker-test

```

There are two essential parts when building a container:

* Dockerfile you probably know
* Build context explanation

```shell
docker build .docker -f .docker/nginx/Dockerfile
                 |      |
                 |      └── use the Dockerfile at ".docker/nginx/Dockerfile"
                 |
                 └── use the .docker subdirectory as build context
```

See makefile commands for more info

* http://localhost/
* [Tutorial](https://www.pascallandau.com/blog/structuring-the-docker-setup-for-php-projects/)
* [Repo from Tutorial](https://github.com/paslandau/docker-php-tutorial)

# cuddly-adventure
