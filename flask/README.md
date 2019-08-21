# Notejam Flask

This contains docker components along with a Makefile to assist in pushing and deploying images to ECR. To read more about the application, please review [README.rst](./README.rst)

## Requirements:

* docker
* docker-compose (local dev env)
* AWS Account (ECS)
* ecs-deploy CLI

## How to run locally

```
# build images
docker-compose build

# run images
docker-compose up
```

## Gotchas

If running for the first time, the app requires setting up the database. The `docker-compose.yml` file is set up in a way to run the database migration once the database is up and running.  However, the database may need a little more time to run so the `docker-compose up` command may need to be re-run.  Once setup, `docker-compose up` will only need to run once (unless docker images are destroyed and need to be recreated)
