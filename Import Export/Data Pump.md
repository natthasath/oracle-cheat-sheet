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

## Table Export/Import
```bash
expdp sys/[password]@orcl tables=[table_name] directory=[directory_name] dumpfile=[table_name].dmp logfile=[table_name].log
impdp sys/[password]@orcl tables=[table_name] directory=[directory_name] dumpfile=[table_name].dmp logfile=[table_name].log
```

## Schema Export/Import
```bash
expdp sys/[password]@orcl schemas=[schema_name] directory=[directory_name] dumpfile=[schema_name].dmp logfile=[schema_name].log
impdp sys/[password]@orcl schemas=[schema_name] directory=[directory_name] dumpfile=[schema_name].dmp logfile=[schema_name].log
```

## Database Export/Import
```bash
expdp sys/[password]@orcl full=Y directory=[directory_name] dumpfile=DB10G.dmp logfile=expdpDB10G.log
impdp sys/[password]@orcl full=Y directory=[directory_name] dumpfile=DB10G.dmp logfile=impdpDB10G.log
```

## Without Password and Directory
```bash
expdp \"/ as sysdba\" as sysdba dumpfile=[file_name].dmp logfile=[table_name].log full=yes ;
impdp \"/ as sysdba\" as sysdba dumpfile=[file_name].dmp logfile=[table_name].log full=yes ;
```

## Credit
