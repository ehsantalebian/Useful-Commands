# MySQL Commands

Here are some sets of MySQL commands that can assist you in your day-to-day activities.

- Login
```bash
mysql -u [User Name] -h [Host Name] -p
```

- Export Dump
```bash
mysqldump -h [Host] -u [User] -p [Name] > [Backup Path.sql]
```

- Export Dump Without Data (Schema Only)
```bash
mysqldump -h [Host] -u [User] -p [Name] --no-data > [Backup Path.sql]
```

- Restore Dump
```bash
mysql -h [Host] -u [User] -p [Name] < [Backup Path.sql]
```

- Create a New Database
```bash
CREATE DATABASE [Database Name] CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```

- Create a Table
```bash
ALTER TABLE [Table Name] CHANGE COLUMN [Column Name] [Column Name];
```

- Create a Column
```bash
ALTER TABLE [Table Name] ADD [Column Name] varchar(255);
```

- Drop a Database
```bash
DROP DATABASE [Database Name]
```

- Drop a Table
```bash
DROP TABLE [Table Name];
```

- Drop a Column
```bash
ALTER TABLE [Table Name] DROP COLUMN [Column Name];
```

- Drop a Row
```bash
DELETE FROM [Table Name] WHERE id=[ID Number];
```

- Search for a Table
```bash
SELECT table_schema, table_name FROM information_schema.tables WHERE table_name LIKE '%[Name]%';
```

- Search for a Table in a Database
```bash
SELECT table_schema, table_name FROM information_schema.tables WHERE table_name LIKE '%[Name]%' AND table_schema = '[Database Name]';
```

- Show DB Character Set and Collation
```bash
SELECT @@character_set_database, @@collation_database;
```

- Show DB Tables Collation
```bash
SELECT table_name, table_collation FROM information_schema.tables WHERE table_schema = '[Database Name]';
```

- Create a New User
```bash
CREATE USER '[User Name]'@'localhost' IDENTIFIED BY '[Password]';
```

- Drop a User
```bash
DROP USER '[User Name]'@'localhost';
```

- Set Root Password
```bash
ALTER USER [User Name]'@'localhost' IDENTIFIED BY '[Password]';
```

- Show User Privilege
```bash
SHOW GRANTS FOR '[User Name]'@'localhost';
```

- Grant Privilege
```bash
GRANT [Privilege Name] ON [Database Name].* TO '[User Name]'@'localhost';
```

- Grant Full Privilege
```bash
GRANT CREATE, ALTER, DROP, INSERT, UPDATE, DELETE, SELECT, REFERENCES, RELOAD on *.* TO '[User Name]'@'localhost';
```

- Revoke Privilege
```bash
REVOKE [Privilege Name] ON [Database Name].* FROM '[User Name]'@'localhost';
```

DBA Truncdrop Commands
- Non-Partitioned Tables
```bash
call dba.truncdrop('DB Name','Table Name','truncate or drop','table','');
```

- Partitioned Tables
```bash
call dba.truncdrop('DB Name','Table Name','truncate or drop','partition','Partition Name');
```
