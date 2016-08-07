# backup-docker-postgresql

Backup from and restore to remote PostgreSQL databases, which are (optionally) running in Docker containers.
 
## Backup with [backupdockerpostgresql](./backupdockerpostgresql)

### Example

```
$ ./backupdockerpostgresql --kill --container postgres user@example.com backup.gz
```

### Usage

```
backupdockerpostgresql [--kill] [--help] [--container <id>] host [backup_file]
```

Flag | Argument | Description
--- | --- | ---
-k, --kill | | Close all other database connections
-c, --container | id or name | The id or name of the Docker container in which PostgreSQL is running. If omitted, then connect to the database running directly on the host.
-h, --help | | Print a help message and exit

Argument | Required |Description
--- | --- | ---
host | ✓ | The remote host to connect to
backup_file | | The optional file to which to save the backup data. If not specified, then the backup data will be written to stdout


## Restore with [restoredockerpostgresql](./restoredockerpostgresql)

### Example

```
$ ./restoredockerpostgresql --kill --container 376064e2a45e user@example.com backup.gz
```

### Usage

```
restoredockerpostgresql [--drop] [--kill] [--help] [--container <id>] host [backup_file]
```

Flag | Argument | Description
--- | --- | ---
-d, --drop | | Drop all non-template databases except for the one named "postgres"
-c, --container | id or name | The id or name of the Docker container in which PostgreSQL is running. If omitted, then connect to the database running directly on the host.
-k, --kill | | Close all other database connections
-h, --help | | Print a help message and exit

Argument | Required |Description
--- | --- | ---
host | ✓ | The remote host to connect to
backup_file | | The optional file from which to read the backup data. If not specified, then the backup data will be read from stdin

