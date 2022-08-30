# Flyway:
Flyway is an open-source database migration tool. It strongly favors simplicity and convention over configuration.

It is based around just 7 basic commands: Migrate, Clean, Info, Validate, Undo, Baseline and Repair.

Migrations can be written in SQL (database-specific syntax (such as PL/SQL, T-SQL, ...) is supported) or Java (for advanced data transformations or dealing with LOBs).
https://flywaydb.org/documentation/

## tasks:

### migrate `flywayMigrate`

Applies DB changes

reads from Vx__files

```shell
Database: jdbc:h2:file:./app/db/database (H2 2)
Successfully validated 2 migrations (execution time 00:00.018s)
Current version of schema "PUBLIC": 1
Migrating schema "PUBLIC" to version 2 - added phone number
Successfully applied 1 migration to schema "PUBLIC" (execution time 00:00.016s)

> Task :app:flywayInfo
Schema version: 2
+-----------+---------+--------------------+------+---------------------+---------+
| Category  | Version | Description        | Type | Installed On        | State   |
+-----------+---------+--------------------+------+---------------------+---------+
| Versioned | 1       | initial schema     | SQL  | 2022-08-30 01:49:34 | Success |
| Versioned | 2       | added phone number | SQL  | 2022-08-30 01:50:39 | Future  |
+-----------+---------+--------------------+------+---------------------+---------+

```
### clean `flywayClean`

Drops everything, disabled by default

```shell
Database: jdbc:h2:C:/scala/projects/flywaydb_sample/app/db/database (H2 2.1)
Successfully dropped pre-schema database level objects (execution time 00:00.000s)
Successfully cleaned schema "PUBLIC" (execution time 00:00.005s)
Successfully cleaned schema "PUBLIC" (execution time 00:00.000s)
Successfully dropped post-schema database level objects (execution time 00:00.000s)


```
### info `flywayInfo`

Displays flyway history and current state

```shell
2:14:16 AM: Executing 'flywayInfo'...


> Task :app:flywayInfo
Schema version: 2
+-----------+---------+--------------------+------+---------------------+---------+
| Category  | Version | Description        | Type | Installed On        | State   |
+-----------+---------+--------------------+------+---------------------+---------+
| Versioned | 1       | initial schema     | SQL  | 2022-08-30 01:49:34 | Success |
| Versioned | 2       | added phone number | SQL  | 2022-08-30 01:50:39 | Future  |
+-----------+---------+--------------------+------+---------------------+---------+

```
### validate `flywayValidate`

Validates all changes are applied on db

```shell
2:21:54 AM: Executing 'flywayValidate'...

> Task :app:flywayValidate

BUILD SUCCESSFUL in 499ms

```
### undo `flywayUndo`

Rollbacks schema changes, reads from Ux__ files

* Proprietary  feature

```shell
Database: jdbc:h2:file:C:\Programs\flyway-0-SNAPSHOT\flyway.db (H2 1.3)
Current version of schema "PUBLIC": 1
Undoing migration of schema "PUBLIC" to version 1 - First
Successfully undid 1 migration to schema "PUBLIC" (execution time 00:00.024s).

```
### baseline `flywayBaseline`

Sets initial database state

```shell
output

```
### repair `flywayRepair`

Removes failed migrations and aligns checksums to the latest successful migration

```shell
Database: jdbc:h2:C:/scala/projects/flywaydb_sample/app/db/database (H2 2.1)
Repair of failed migration in Schema History table "PUBLIC"."flyway_schema_history" not necessary. No failed migration detected.
Successfully repaired schema history table "PUBLIC"."flyway_schema_history" (execution time 00:00.017s).


```