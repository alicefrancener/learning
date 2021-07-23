# PostgreSQL

## Connecting to the PSQL server via Docker/CLI
[How To Install and Run PostgreSQL using Docker ?][postgresql-01]

1. Find the docker-container-id in which the postgres is running: `docker ps -a`
2. Enter into the container with the container ID: `docker exec -it <PSQL-Container-ID> bash`
3. Authenticate to start using as postgres user: `psql -h localhost -p 5432 -U postgres -W`
4. Enter the password used while creating the PSQL server container

<!--- References --->

[postgresql-01]: https://dev.to/shree_j/how-to-install-and-run-psql-using-docker-41j2
