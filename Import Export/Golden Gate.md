# Oracle Database
Documentation for Oracle DBA beginner
```bash

```

# Table of Content

* Create Database
* Start Stop Service
* Network Connection
* Database Interface
* Storage Structure
* User and Security
* SQL*Plus Command
* Oracle Cheat Sheet

## SQL*Plus Command

Access SQL*Plus
```bash
sqlplus /nolog
```

Connect
```bash
SQL> connect / as sysdba
SQL> connect sys/[password]@[ORACLE_SID] as sysdba
```

Start Database
```bash
SQL> startup
SQL> startup pfile=''
```

Stop Database
```bash
SQL> shutdown immediate
```

Check Instance
```bash
SQL> select instance_name, status from v$instance ;
```

Show Date
```bash
SQL> select sysdate from dual ;
```

Show SGA
```bash
SQL> show sga
```

Show User tables
```bash
SQL> select table_name from user_tables order by 1 ;
```

Show Parameter
```bash
SQL> show parameter
SQL> show parameter process
```

Show Path Datafile
```bash
SQL> select name from v$datafile;
```

Create SPfile from Pfile
```bash
SQL> create pfile from spfile ;
```

Update Pfile from SPfile
```bash
SQL> create spfile from pfile
```

History
```bash
SQL> set history on
SQL> show history
SQL> history [number] run
SQL> history [number] edit
SQL> clear history
```

## Command Cheat Sheet

Listener
```bash
lsnrctl status
lsnrctl start
lsnrctl stop
```

TNSPING
```bash
tnsping orcl
```

Enterprise Manager
```bash
emctl status dbconsole
emctl start dbconsole
emctl stop dbconsole
emctl getemhome
```

Alert Log
```bash
$ORACLE_BASE/diag/rdbms/orcl/orcl/trace/alert_orcl.log
```

TNSNAMES
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

Listener
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

Uninstall
```bash
$ORACLE_HOME/deinstall/deinstall
```

## Failed Error

Failed Start Listener
```bash
ไม่สามารถ Start Listener ได้ ให้ไปดูที่ไฟล์ listener ว่า config hostname และ port ถูกต้องหรือไม่
```

Filed Start Database (pfile)
```bash
ไม่สามารถ Start Database ได้ ให้ไปสร้างไฟล์ pfile จาก spfile

create pfile from spfile='/u01/app/oracle/product/11.2.0/db_1/dbs/spfileorcl.ora' ;
```

Failed Start Enterprise Manager
```bash
ไม่สามารถ Start Enterprise Manager ได้ ให้ไปแก้ชื่อไฟล์ 2 ที่ ของเดิม hostname เป็น localdomain และ ORACLE_SID เป็น orcl
$ORACLE_HOME/oc4j/j2ee/OC4J_DBConsole_ol6.lab.local_DB11G/
$ORACLE_HOME/ol6.lab.local_DB11G

หากยังไม่ได้ให้ทำการ Rebuild Enterprise Manager
```

## Credit
