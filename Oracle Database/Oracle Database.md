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
* SQLPlus Command
* Oracle Cheat Sheet

## SQLPlus Command

Access SQL*Plus
```bash
sqlplus /nolog
```

Connect
```bash
SQL> connect / as sysdba
SQL> connect sys/[password]@orcl as sysdba
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

Show Parameter
```bash
SQL> show parameter
SQL> show parameter process
```

Create SPfile from Pfile
```bash
SQL> create pfile from spfile ;
```

Update Pfile from SPfile
```bash
SQL> create spfile from pfile
```

## Command Cheat Sheet

Listener
```bash
lsnrctl status
lsnrctl start
lsnrctl stop
```

Enterprise Manager
```bash
emctl status dbconsole
emctl start dbconsole
emctl stop dbconsole
```

Alert Log
```bash
$ORACLE_HOME/diag/rdbms/orcl/orcl/trace/alert_orcl.log
```

Uninstall
```bash
$ORACLE_HOME/deinstall/deinstall
```

## Credit
