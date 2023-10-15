# POSTGRES AND PGADMIN CONTAINERS

The purpose for this project is to create a postgres database container and pgadmin container to manage the database created.

Both containers are created using docker-compose from the docker-compose.yml file which has been defined.

In the following sections, the differents steps to follow are explained

## CREATE docker-compose.yml file

This file defines the configuration for both containers. The both containers are defined in the section named as **services**.

For the case of postgres services, the configuration used is the following:

- **image:** In this case we choose the latest version available for postgres image in docker hub.
- **restart:** It means that in case of failure, the container must restart again.
- **ports:** Indicate the port binding from the external port to the internal port. In this case we use the normal port for this cases: 5432
- **environment:** Defines the environment variables and its values which are needed to run the container.
- **volumes:** Indicates the path inside the container where we are going to store the db data. It means that while we don´t remove the container, the info will be always accesible. Furthermore, in the volumes section we define the schema.sql which will be used at the beginning, when the container is created. It permits predefined the tables which we need to add to the database, even, we can add more sql files to execute insert queries in the initialization of the container.


For the case of pgadmin services, the configuration used is the following:

- **image:** In this case we choose the latest version available for postgres pgadmin in docker hub.
- **ports:** Indicate the port binding from the external port to the internal port. In this case we use port 80.
- **environment:** Defines the environment variables and its values which are needed to run the container. In this case, the email and password could be invented. But it is the one which must be used to login in pdadmin web.
- **depends_on:** Indicate that the pgadmin service depends on the postgres services. For that reason, postgres will start before than pgadmin.

## RUN containers

Open a terminal in the same directory where docker-compose.yml file is and run the following command.

```
docker-compose build
```


```
docker-compose up
```

For the first time that you run it, it is normal that it spends some time downloading all the information related to the images used to build the containers.

### POSTGRES CONSIDERATIONS

 - When the docker-compose up command is run, a new folder must be created in the directory project, in this folder is where information related to the tables inside of the database are stored. If you delete the folder, you remove all the data you had added.

 - If you want to modify the initialization schema, you must previously delete the **postgres_data folder**, otherwise, initialization will not be executed when creating the docker container.

### PGADMIN CONSIDERATIONS

After creating both containers:

- To access  pgadmin page you must search on google: **localhost:port** (in this case, as we used port 80, using localhost is enough).

- Once you have login inside pgadmin. To stablish connection with the database created, in the field host, you must write **postgres** instead of localhost because although the container is running in localhost, the application is inside the postgres container.