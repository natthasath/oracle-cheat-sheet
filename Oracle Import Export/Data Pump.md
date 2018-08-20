# Oracle Data Pump
Oracle Data Pump is a new feature of Oracle Database 10g and later. A new public interface package, DBMS_DATAPUMP, provides a server-side infrastructure for fast data and metadata movement between Oracle databases. It is ideal for large databases and data warehousing environments, where high-performance data movement offers significant time savings to database administrators.

Data Pump automatically manages multiple, parallel streams of unload and load for maximum throughput. The degree of parallelism can be adjusted on-the-fly. There are new and easy-to-use Export and Import utilities (expdp and impdp), as well as a web-based Enterprise Manager export/import interface.

Data Pump is an integral feature of Oracle Database 11g Release 2 and is available in all configurations. However, parallelism is available only in Enterprise Edition.

## Privileged users
* Export and import database objects owned by others
* Export and import nonschema-based objects such as tablespace and schema definitions, system privilege grants, resource plans, and so forth
* Attach to, monitor, and control Data Pump jobs initiated by others
* Perform remapping operations on database datafiles
* Perform remapping operations on schemas other than their own

## Defualt Path
```bash
SQL> select directory_name, directory_path from dba_directories where directory_name = 'DATA_PUMP_DIR' ;
```

## Table Export/Import
```bash
expdp sys/[password]@orcl tables=[table_name] directory=[directory_name] dumpfile=[table_name].dmp logfile=expdp[table_name].log
impdp sys/[password]@orcl tables=[table_name] directory=[directory_name] dumpfile=[table_name].dmp logfile=impdp[table_name].log
```

## Schema Export/Import
```bash
expdp sys/[password]@orcl schemas=[schema_name] directory=[directory_name] dumpfile=[schema_name].dmp logfile=expdp[schema_name].log
impdp sys/[password]@orcl schemas=[schema_name] directory=[directory_name] dumpfile=[schema_name].dmp logfile=impdp[schema_name].log
```

## Database Export/Import
```bash
expdp sys/[password]@orcl full=Y directory=[directory_name] dumpfile=orcl.dmp logfile=expdp_orcl.log
impdp sys/[password]@orcl full=Y directory=[directory_name] dumpfile=orcl.dmp logfile=impdp_orcl.log
```

## Parameter Export/Import
```bash
expdp sys/[password]@orcl full=Y directory=[directory_name] parfile=porcl.par logfile=expdp_porcl.log
impdp sys/[password]@orcl full=Y directory=[directory_name] parfile=porcl.par logfile=impdp_porcl.log
```

## Without Password and Directory

Default directory is $ORACLE_BASE/admin/[ORACLE_SID]/dpdump/[file_name].dmp

```bash
expdp \"/ as sysdba\" dumpfile=[file_name].dmp logfile=[table_name].log full=yes
impdp \"/ as sysdba\" dumpfile=[file_name].dmp logfile=[table_name].log full=yes
```

## Impdp Parameter

* TABLE_EXISTS_ACTION

This action of import data when the table already exists in the database, the default value is skip.
```bash
TABLE_EXISTS_ACTION = {SKIP | APPEND | TRUNCATE | REPLACE}
- SKIP (Default)    skip table already exists in the database, it is invalid if you set content=data_only
- APPEND            add new rows but number and type of data must match, it is default when you set content=data_only
- TRUNCATE          replace rows when columns of data not match, not use with db link or cluster table
- REPLACE           replace definition and rows when columns of data not match
```

## Credit
https://oracle-base.com/articles/10g/oracle-data-pump-10g

## License
Codeinsane license.