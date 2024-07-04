# docker-assignment

A simple exercise for using the Docker platform

## Working with the SmartShark dataset

SmartShark is a dataset with data on the evolution of a set of open source projects. For each project the dataset includes information about all commits, diffs for each commits as well as metrics, refactorings, bugs, issues etc.

Working with the [SmartShark](https://smartshark2.informatik.uni-goettingen.de/) dataset requires restoring a MongoDB database back up file to the researchers local development environment. The inspection of the database contents after its restore requires an appropriate front-end application and [mongo-express](https://github.com/mongo-express/mongo-express) is a good alternative.

Experimentation with the dataset and development of appropriate analysis procedures can be supported with a distribution of [Jupyter Notebook](https://jupyter.org/).

## Assignment: preparation of the experimentation environment

As part of the assignment prepare appropriate Dockerfiles, a docker-compose.yml manifest file and shell scripts, if required, for easy setup of an environment for experimenting and analyzing the SmartShark data. As part of preparing the Docker, you can take into account the following requirements:

### SmartShark utility library and data files

Analysis of the SmartShark dataset is supported with the pycoshark Python library, which can be easily installed with pip, i.e. `pip install pycoshark`.

The small version of the SmartShark dataset is available from the following location: https://data.goettingen-research-online.de/download/smartshark_2_2_small.agz

### MongoDB docker image

As part of the assignment you can use the `mongo:7.0.11` docker image. The specific MongoDB distribution stores data files in the following directories:

* `/data/configdb`
* `/data/db`

Configuration of the MongoDB docker image is based on the following environment variables:

* MONGO_INITDB_ROOT_USERNAME: username for the MongoDB admin user,
* MONGO_INITDB_ROOT_PASSWORD: password for the MongoDB admin.

Finally, MongoDB uses as default port, the port 27017.

Restoration of the database backup file can be executed on a running database with the following command:

```
mongorestore -u {admin-user} -p {admin-password} --authenticationDatabase admin --gzip --archive={archive path in the db host}
```



### MongoExpress docker image

MongoExpress can be locally deployed with the `mongo-express:1.0.2-20-alpine3.19` docker image. Basic configuration for using the image involves the following environment variables:

* ME_CONFIG_MONGODB_ADMINUSERNAME: username of the MongoDB admin,
* ME_CONFIG_MONGODB_ADMINPASSWORD: password for the MongoDB admin,
* ME_CONFIG_MONGODB_URL: connect string for the database of the form: `mongodb://{admin-username}:{admin-password}@{db-hostname}:27017/`
* ME_CONFIG_BASICAUTH: Use of Basic Authentication method (false).

### Jupyter notebooks docker image

Jupyter notebooks can be locally deployed by using the docker image `quay.io/jupyter/base-notebook:python-3.11.9`.


