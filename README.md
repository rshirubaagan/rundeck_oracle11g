# Rundeck and Oracle XE 11g Docker environment

This is a Docker Compose example to run Rundeck + Oracle 11g as a backend.

To run, follow these steps:

1) Start the Oracle container: `docker compose up -d oracle` (this action may take a few minutes, be patient).

2) Connect to the container: `docker exec -it <oracle_container_name> bash`

3) Then do `su - oracle` and later start SQLPLUS: `sqlplus / as sysdba`

4) Under SQLPLUS, execute the following commands:

```sql
create USER rundeck IDENTIFIED BY rundeck;
GRANT CONNECT, RESOURCE, DBA TO rundeck;
```

5) Exit SQLPLUS with the `Ctrl+D` key combination and exit the oracle/root session using the `exit` command.

6) Now start Rundeck container: `docker compose up -d rundeck` (this action takes around a minute, it depends on your PC/Mac performance).

7) Open your favorite browser (no IE please!) and access the following URL: `http://localhost:4440`, user: `admin`, password: `admin`.

You can learn more about Rundeck [here](https://docs.rundeck.com/docs/about/introduction.html).

And more about Oracle [here](https://docs.rundeck.com/docs/administration/configuration/database/oracle.html#using-oracle-as-a-database-backend).

Cheers.
