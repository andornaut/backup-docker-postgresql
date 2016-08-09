# backup-docker-postgresql

Backup from and restore to local or remote PostgreSQL databases, which are (optionally) running in Docker containers.
 
## Backup with [backupdockerpostgresql](./backupdockerpostgresql)

### Example

```
$ ./backupdockerpostgresql --kill --host user@example.com --container postgres backup.gz
```

### Usage

```
backupdockerpostgresql [--help] [--kill] [--host <hostname>] [--container <id>] [backup_file]
```

Flag | Argument | Description
--- | --- | ---
-c, --container | id or name | The id or name of the Docker container in which PostgreSQL is running. If omitted, then connect to the database running directly on the host.
-h, --host | hostname | The remote host to connect to
-k, --kill | | Close all other database connections
--help | | Print a help message and exit

Argument | Required |Description
--- | --- | ---
backup_file | no | The optional file to which to save the backup data. If not specified, then the backup data will be written to stdout


## Restore with [restoredockerpostgresql](./restoredockerpostgresql)

### Example

```
$ ./restoredockerpostgresql --kill --host user@example.com --container 376064e2a45e backup.gz
```

### Usage

```
restoredockerpostgresql [--help] [--drop] [--kill] [--host <hostname>] [--container <id>] [backup_file]
```

Flag | Argument | Description
--- | --- | ---
-c, --container | id or name | The id or name of the Docker container in which PostgreSQL is running. If omitted, then connect to the database running directly on the host.
-d, --drop | | Drop all non-template databases except for the one named "postgres"
-h, --host | hostname | The remote host to connect to
-k, --kill | | Close all other database connections
--help | | Print a help message and exit

Argument | Required |Description
--- | --- | ---
backup_file | no | The optional file from which to read the backup data. If not specified, then the backup data will be read from stdin

