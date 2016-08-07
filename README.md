# backup-docker-postgresql

Backup from and restore to PostgreSQL databases that are running in Docker containers.

## Instructions
 
[backupdockerpostgresql](./backupdockerpostgresql)

```
./backupdockerpostgresql [--kill] [--help] host container [backup_file]
```

| Flag | Description |
| --- | --- |
| -k, --kill | Close all other database connections |
| -h, --help | Print a help message and exit |

| Argument | Required |Description |
| --- | --- | --- |
| host | ✓ | The remote host to connect to |
| container | ✓ | The id or name of the Docker container in which PostgreSQL is running |
| backup_file | | The optional file to which to save the backup data. If not specified, then the backup data will be written to stdout |


[restoredockerpostgresql](./restoredockerpostgresql) scripts.

```
./restoredockerpostgresql [--drop] [--kill] [--help] host container [backup_file]
```

| Flag | Description |
| --- | --- |
| -d, --drop | Drop all non-template databases except for the one named "postgres" |
| -k, --kill | Close all other database connections |
| -h, --help | Print a help message and exit |

| Argument | Required |Description |
| --- | --- | --- |
| host | ✓ | The remote host to connect to |
| container | ✓ | The id or name of the Docker container in which PostgreSQL is running |
| backup_file | | The optional file from which to read the backup data. If not specified, then the backup data will be read from stdin |

