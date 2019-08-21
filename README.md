# NOTEJAM

## Requirements

* docker (18.06+)
* docker-compose (3+)
* make

For deploying from local machine:

* AWS CLI Credentials
* ecs-deploy (https://github.com/silinternational/ecs-deploy)

## Local Dev

### Docker

```
# build images
docker-compose build

# run images
docker-compose up
```

### Local Machine

If a Database has been configured, you can set these environment variables:

* MYSQL_HOST
* MYSQL_DATABASE
* MYSQL_USER
* MYSQL_PASSWORD

There are default settings if these are not set and can be found in [config.py(./flask/notejam/config.py)]

```
# on Ubuntu, you may need some OS dependencies
sudo apt update && apt install -y default-libmysqlclient-dev

# Set up a virtualenv with python 2.7.x and activate it

# install python depedencies
cd flask
pip install -r requirements.txt

python runserver.py
```

### TESTS

If using `docker`, you can run tests:

```
# build base image
make build

# tests
make tests
```

In local environment, within your virtualenv, run `python tests.py` in the `flask` directory

### Gotchas

If running for the first time, the app requires setting up the database. The `docker-compose.yml` file is set up in a way to run the database migration once the database is up and running.  However, the database may need a little more time to run so the `docker-compose up` command may need to be re-run.  Once setup, `docker-compose up` will only need to run once (unless docker images are destroyed and need to be recreated)

## Deployments

In order to trigger deployment, create a branch and merge into `master`. That is the only condition that will trigger a build.
