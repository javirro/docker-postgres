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


For the case of pgadmin services, the configuration used is the following:

- **image:** In this case we choose the latest version available for postgres pgadmin in docker hub.
- **ports:** Indicate the port binding from the external port to the internal port. In this case we use port 80.
- **environment:** Defines the environment variables and its values which are needed to run the container. In this case, the email and password could be invented. But it is the one which must be used to login in pdadmin web.
- **depends_on:** Indicate that the pgadmin service depends on the postgres services. For that reason, postgres will start before than pgadmin.