# Oracle Clone
Docmentation Clone Oracle Database for step by step
```bash

```

# Table of Content

* Change LISTENER
* Change TNSNAMES
* Change Hosts File
* Change Hostname File

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

## Credit
