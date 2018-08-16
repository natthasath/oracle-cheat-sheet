# Oracle Data Pump
Data pump is a server based technology which enables very high speed import and export data (expdp / impdp)
```bash

```

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