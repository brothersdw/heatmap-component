# Heat Map Component (Dockerized Heat Map)

This repo is for the Dockerized version of the Heat Map API and Frontend

## Getting started

```shell script
git clone https://github.com/brothersdw/heatmap-component.git
```

### Setting up dependencies

- Import submodules

```shell script
cd heatmap-component
./init.sh
```

- Copy `knexfile-example` in `heatmap-api`:
  - Once you have copied the file you will need to configure it using the values from the `mysql` service in `docker-compose.yml`. You can also change these values to anything you want in the `docker-compose.yml` file just make sure what you enter is also reflected in `knexfile.js`.

```shell script
cd heatmap-api
cp knexfile-example.js knexfile.js
```

- Copy `tokens-example` in `heatmap`:
  - After copying this file you will need to grab a public token from your account at https://mapbox.com and place it in the file.

```shell script
cd ../heatmap
cp tokens-example.js tokens.js
```

### Starting application

```shell script
cd ..
docker-compose up
```

#### For reference if any new migrations are needed in the future

To create a new migration script, run the below command:

- This will create a migration script in the `./migrations` folder.
- The name format is `yyyyMMddhhmmss_table_name`.

```shell script
docker exec {container_name} sh -c 'npx knex migrate:make create_{table_name}'
```

To run all migration scripts that have not yet been run, run the below command:

```shell script
docker exec {container_name} sh -c 'npx knex migrate:latest'
```

To rollback all changes, run the below command:

```shell script
docker exec {container_name} sh -c 'npx knex migrate:rollback'
```
