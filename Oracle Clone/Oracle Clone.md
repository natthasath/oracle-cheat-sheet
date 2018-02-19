# Oracle Clone Database
Docmentation clone Oracle Database for step by step
```bash

```

# Table of Content

* Preparing to Clone Database
* Change LISTENER
* Change TNSNAMES
* Change Hosts File
* Change Hostname File

## Preparing to Clone Database

* Flash Recovery Area
```bash
SQL> select * from v$recovery_file_dest ;
SQL> select * from v$recovery_area_usage ;
```

## Change LISTENER
```bash
$ORACLE_HOME/network/admin/listener.ora

LISTENER =
  (DESCRIPTION_LIST =
    (DESCRIPTION =
      (ADDRESS = (PROTOCOL = TCP)(HOST = ol6.lab.local)(PORT = 1521))
    )
  )

ADR_BASE_LISTENER = /u01/app/oracle
```

## Check Service LISTENER
```bash
ORCL
ORCLXDB
```

## Change TNSNAMES
```bash
$ORACLE_HOME/network/admin/tnsnames.ora

ORCL =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = ol6.lab.local)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = orcl)
    )
  )
```

## Change Hosts File
```bash
/etc/hosts
```

## Change Hostname File
```bash
/etc/hostname
```

## Rebuild EM Configuration
```bash
emca -deconfig dbcontrol db -repos drop
```

## Export Database
```bash
expdp \"/ as sysdba\" DUMPFILE=orcl.dmp LOGFILE=export_orcl.log FULL=YES ;
```

## SCP Copy
```bash
scp orcl.dmp oracle@ol6.lab.local:/u01/app/oracle/admin/orcl/dpdump
```

## Import Database
```bash
impdp \"/ as sysdba\" DUMPFILE=orcl.dmp LOGFILE=export_orcl.log FULL=YES ;
```

## Credit
http://www.dba-oracle.com/tips_oracle_export_utility.htm