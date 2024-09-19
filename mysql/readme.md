
## Get database from remote host
``` bash
#!/bin/bash
# tested on aws RDS
# exec to get file .sql with db
mysqldump -h <host> \                                               
    -u <username> \
    -p '<database_name>' \
    --port=3306 \
    --single-transaction \
    --routines \
    --triggers \
    --databases <db_name> > ./db-dump.sql
# this command showed errors when importing
# stored procedures in docker image
# share if you know the solution for this problem
```

## Start container
``` bash
# build
docker compose up -d --build

# watch logs
docker compose logs -f db

# if not start try start and watch logs
docker compose start db

# finally try to connect to your container
mysql -h localhost -P 3306 -u root -p <db_name>

# now that the container is built we only have to start it with the
# start command to avoid losing data.

```