# Oracle Database
Documentation for Oracle DBA beginner
```bash

```

# Table of Content

* Create Listener
* Create Database
* Create Alias
* Start Stop Service
* Network Connection
* Database Interface
* Storage Structure
* User and Security
* SQL*Plus Command
* Oracle Cheat Sheet

## Create Listener

* NETCA (Net Configuration Assistant)
```bash
$ cd $ORACLE_HOME/bin/
$ netca
```

## Create Database

* DBCA (Database Configuration Assistant)
```bash
$ cd $ORACLE_HOME/bin/
$ ./dbca
```

* Database Character Set
```bash
TH8TISASCII - Thai Industrial Standard
```

* Generate Database Create Script
```bash
$ cd $ORACLE_BASE/admin/$ORACLE_SID/scripts
```

* Save Report Create Database
```bash
$ cd $ORACLE_HOME/bin
```

## Create Alias
```bash
$ vi .bash_profile
-----------------------------
alias network='cd $ORACLE_HOME/network/admin'
alias trace='cd $ORACLE_BASE/diag/rdbms/$ORACLE_SSID/$ORACLE_SID/'

alias alert='tail -100 $DBA/$ORACLE_SID/bdump/alert_$ORACLE_SID.log|more'
alias arch='cd $DBA/$ORACLE_SID/arch'
alias bdump='cd $DBA/$ORACLE_SID/bdump'
alias cdump='cd $DBA/$ORACLE_SID/cdump'
alias pfile='cd $DBA/$ORACLE_SID/pfile'
alias udump='cd $DBA/$ORACLE_SID/udump'
alias rm='rm -i'
alias sid='env|grep -i sid'
alias admin='cd $DBA/admin'
alias logbook='/u01/app/oracle/admin/$ORACLE_SID/logbook'
-----------------------------
$ . ~/.bash_profile
```

## SQL*Plus Command

#### Access Database
* Access not login
```bash
sqlplus /nolog
```

* Access login as sysdba
```bash
sqlplus / as sysdba
```

* Connect Database in SQL*Plus
```bash
SQL> conn / as sysdba
SQL> connect / as sysdba
SQL> connect sys/[password] as sysdba
SQL> connect sys/[password]@[ORACLE_SID] as sysdba
```

#### Start Stop Database
* Start Database
```bash
SQL> startup
SQL> startup pfile=''
```

* Stop Database
```bash
SQL> shutdown immediate
```

#### Check Connection Database
* Check User
```bash
SQL> show user ;
```

* Check Instance
```bash
SQL> select instance_name, status from v$instance ;
```

* Check Date
```bash
SQL> select sysdate from dual ;
```

#### Check Views and Tables Database
* Check Object
```bash
SQL> select owner, object_name from all_objects ;
SQL> select count(object_id) as sum from all_objects ;
SQL> select count(object_id) as sum, object_type from all_objects group by object_type order by object_type asc ;
SQL> select count(object_id) as sum, object_type from all_objects where object_type = 'TABLE' group by object_type ;
SQL> select count(object_id) as sum, object_type from all_objects where object_type = 'VIEW' group by object_type ;
SQL> select count(object_id) as sum, owner from all_objects where object_type = 'TABLE' group by owner ;
SQL> select count(object_id) as sum, owner from all_objects where object_type = 'VIEW' group by owner ;
```

#### Show Parameters
* Show Parameter
```bash
SQL> show parameter
SQL> show parameter process
```

* Show SGA
```bash
SQL> show sga
```

* Show Database Buffer Cache
```bash
SQL> show db_cache_size
```

* Show Shared Pool
```bash
SQL> show shared_pool_size
```

* Show Redo Log Buffer
```bash
SQL> show log_buffer
```

#### Manage Users
* Create User
```bash
SQL> create user demo identified by 1234 ;
```

* Grant Privilege User
```bash
SQL> grant session to demo ;
```

* Show All Users
```bash
SQL> select user_id, username, created from all_users ;   ## View all users of current user
SQL> select user_id, username, created from dba_users ;   ## View all users of database and contains more columns than all_users
SQL> select user_id, username, created from user_users ;  ## View current user and contains more columns than all_users
```

* Show Default Tablespace User
```bash
SQL> select user_id, username, default_tablespace from dba_users ;
```

* Show User Table
```bash
SQL> select table_name from user_tables order by 1 ;
```

* Show Tablespace
```bash
SQL> select tablespace_name from user_tablespaces ;
```

* Change Password
```bash
SQL> alter user demo identified by 1234 ;
```

## Manage Object
* Create Synonym
```bash
SQL> create synonym emp for scott.emp ;
```

#### Manage pfile and spfile
* Show Path Datafile
```bash
SQL> select name from v$datafile ;
```

* Create spfile from pfile
```bash
SQL> create pfile from spfile ;
```

* Update pfile from spfile
```bash
SQL> create spfile from pfile
```

#### Log
* History Query
```bash
SQL> set history on
SQL> show history
SQL> history [number] run
SQL> history [number] edit
SQL> clear history
```

## Oracle Cheat Sheet

* LISTENER
```bash
lsnrctl status
lsnrctl start
lsnrctl stop
```

* TNSPING
```bash
tnsping orcl
```

* Enterprise Manager
```bash
emctl status dbconsole
emctl start dbconsole
emctl stop dbconsole
emctl getemhome
```

* Alert Log
```bash
$ORACLE_BASE/diag/rdbms/orcl/orcl/trace/alert_orcl.log
```

* TNSNAMES
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

* LISTENER
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

* Uninstall
```bash
$ORACLE_HOME/deinstall/deinstall
```

## Failed Error

* Failed Start Listener
```bash
ไม่สามารถ Start Listener ได้ ให้ไปดูที่ไฟล์ listener ว่า config hostname และ port ถูกต้องหรือไม่
```

* Filed Start Database (pfile)
```bash
ไม่สามารถ Start Database ได้ ให้ไปสร้างไฟล์ pfile จาก spfile

create pfile from spfile='/u01/app/oracle/product/11.2.0/db_1/dbs/spfileorcl.ora' ;
```

* Failed Start Enterprise Manager
```bash
ไม่สามารถ Start Enterprise Manager ได้ ให้ไปแก้ชื่อไฟล์ 2 ที่ ของเดิม hostname เป็น localdomain และ ORACLE_SID เป็น orcl
$ORACLE_HOME/oc4j/j2ee/OC4J_DBConsole_ol6.lab.local_DB11G/
$ORACLE_HOME/ol6.lab.local_DB11G

หากยังไม่ได้ให้ทำการ Rebuild Enterprise Manager
emctl stop dbconsole
emca -deconfig dbcontrol db
emca -repos recreate
```

* Failed Stop Database
```bash
ไม่สามารถ Stop Database ได้ เพราะยังไม่ได้ Start
SQL> shutdown immediate
ORA-01034: ORACLE not available
ORA-27101: shared memory realm does not exist
Linux-x86_64 Error: 2: No such file or directory
```

## Credit
http://www.dba-oracle.com/
https://docs.oracle.com/cd/B28359_01/em.111/b31207/oui7_opatch.htm#CEGCJGJD