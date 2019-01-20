# zMS Private Server

Docker orchestration for an OdinMS-based private server.
Note that this repo is unusable without a proper repack and related tools.

Simply...

* setup the containers with a proper repack
* configure through `.env` file
* `docker-compose up`

## Database

### Setup

A repack typically comes with a set of SQL scripts to initialize the database.
Copy these into `/src/db/ms-sql`. 
If the server initializes without a database, these will be run in alphanumeric order.

The following variables from `.env` will be available:

|Key|Default|Purpose|
|---|---|---|
|`MYSQL_DATABASE`|`odinms`|MySQL database name|
|`MYSQL_ROOT_PASSWORD`|`root`|MySQL root password|

### Runtime

MySQL database files are stored in the `/data` directory.

The `db` will be exposed in the following ways:

* externally, for direct connection through [dbeaver](https://dbeaver.io/), at port `3306`
* within the Docker network at: `mysql://db:3306`

## Server

### Setup

Copy the server files into `/src/server/ms-server`.
Include a repack-specific "bootstrap" script, named `zms-start.sh`.
This will typically edit the `*.properties` files based on environment variables and kick-off the server processes.

The following variables from `.env` will be available:

|Key|Default|Purpose|
|---|---|---|
|`MYSQL_DATABASE`|`odinms`|MySQL database name (see `db.properties`)|
|`MYSQL_ROOT_PASSWORD`|`root`|MySQL root password (see `db.properties`)|
|`ZMS_HOST`|`localhost`|Endpoint where client can login (see `world.properties`)|

### Runtime

The `server` will expose ports 8484 (world server) and 7575-7578 (channel servers).
