# Oracle Database
Documentation for Oracle DBA beginner
```bash

```

# Table of Content
* Create & Delete Listener
* Create & Delete Database
* Create Alias
* Start Stop Service
* Network Connection
* Database Interface
* Storage Structure
* User and Security
* SQL*Plus Command
* RMAN Command
* Oracle Cheat Sheet

## Create & Delete Listener
* NETCA (Net Configuration Assistant)
```bash
$ cd $ORACLE_HOME/bin/
$ netca
```

## Create & Delete Database
* DBCA (Database Configuration Assistant)
```bash
$ cd $ORACLE_HOME/bin/
$ ./dbca
```

* Database Template
```bash
- Transaction Processing (Default)      include datafiles
- Custom Database                       not include datafiles
- Data Warehouse                        include datafiles
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

* Delete Database
```bash
$ cd $ORACLE_HOME/bin/
$ ./dbca
$ rm -rf /etc/oratab
```

## Create Alias
```bash
$ vi .bash_profile
-----------------------------
alias archive='cd /u01/app/oracle/flash_recovery_area/$ORACLE_SID/'
alias network='cd $ORACLE_HOME/network/admin'
alias trace='cd $ORACLE_BASE/diag/rdbms/$ORACLE_SSID/$ORACLE_SID/'

alias gg='cd /data/ggate'
alias RMAN_LOG='cd /usr/openv/netbackup/ext/db_ext/oracle/samples/rman'
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

#### SET
```bash
SQL> set pages 100
SQL> set lines 120
SQL> set linesize 300
SQL> column column_name format a30
```

#### Access Database
* Access not login
```bash
$ sqlplus
$ sqlplus /nolog
```

* Access login as sysdba
```bash
$ sqlplus / as sysdba
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

* Check Open Mode
```bash
SQL> select name, open_mode from v$database ;
```

* Check Datafile
```bash
SQL> select name from v$datafile ;
```

* Check Control File
```bash
SQL> select name from v$log ;
SQL> select group#, status from v$log;
```

#### Check Date
```bash
SQL> select sysdate from dual ;
```

#### Check Features
```bash
SQL> select name, detected_usages from dba_feature_usage_statistics where detected_usages > 0 ;
```

#### Check Character SET
```bash
SQL> select * from nls_database_parameters ;
```

#### Check Session
```bash
SQL> select * from v$lock ;
```

### Check Jobs Status
```bash
SQL> select job, log_user, schema_user, failures from dba_jobs ;
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

#### Check Sequence Number
```bash
http://www.dba-oracle.com/t_oracle_nextval_function.htm
SQL>
```

#### Check Archive Log
```bash
SQL> archive log list
SQL> show parameter db_recovery_file_dest
SQL> select dest_name, status, destination from v$archive_dest ;
```

#### Check DB Size
```bash
SQL> select sum(bytes)/1024/1024 size_in_mb from dba_data_files ;
SQL> select sum(bytes)/1024/1024 size_in_mb from dba_segments ;
SQL> select owner, sum(bytes)/1024/1024 Size_MB from dba_segments group  by owner ;
```

#### Check License
```bash
SQL> select name, version, description, detected_usages, last_usage_date from dba_feature_usage_statistics where name like 'Automatic Workload%' or name like 'AWR%';
```

#### Check Version
```bash
SQL> select * from v$version ;
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
SQL> select name, value/1024/1024 "SGA (MB)" from v$sga ;
SQL> select sum(value)/1024/1024 "TOTAL SGA (MB)" from v$sga ;
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

#### Resize Parameter
* Resize FRA
```bash
SQL> show parameter db_recovery_file_dest_size
SQL> alter system set db_recovery_file_dest_size = 20g scope=both sid='*';
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
* Show Object
```bash
SQL> select count(object_name), object_type from dba_objects where owner like group by object_type ;
```

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

## RMAN Command
* Report Schema
```bash
RMAN> report schema ;

using target database control file instead of recovery catalog
Report of database schema for database with db_unique_name orcl

List of Permanent Datafiles
===========================
File Size(MB) Tablespace           RB segs Datafile Name
---- -------- -------------------- ------- ------------------------
1    670      SYSTEM               ***     /u01/app/oracle/oradata/orcl/system01.dbf
2    470      SYSAUX               ***     /u01/app/oracle/oradata/orcl/sysaux01.dbf
3    25       UNDOTBS1             ***     /u01/app/oracle/oradata/orcl/undotbs01.dbf
4    5        USERS                ***     /u01/app/oracle/oradata/orcl/users01.dbf

List of Temporary Files
=======================
File Size(MB) Tablespace           Maxsize(MB) Tempfile Name
---- -------- -------------------- ----------- --------------------
1    20       TEMP                 32767       /u01/app/oracle/oradata/orcl/temp01.dbf
```

* Report Backup
```bash
RMAN> list backup summary ;
```

## Oracle Cheat Sheet
* Firewall
```bash
service iptables start
chkconfig iptables on
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 1158 -j ACCEPT
iptables -A INPUT -p tcp --dport 1521 -j ACCEPT
iptables -A INPUT -p tcp --dport 5501 -j ACCEPT
chkconfig --level 345 iptables on
service iptables save
service iptables status

iptables -D INPUT 11

https://oracle-base.com/articles/linux/linux-firewall
```

* LISTENER
```bash
$ lsnrctl status
$ lsnrctl start
$ lsnrctl stop
$ lsnrctl reload
```

* Enterprise Manager
```bash
$ emctl status dbconsole
$ emctl start dbconsole
$ emctl stop dbconsole
$ emctl getemhome
```

* CRSCTL
```bash

```

* TNSPING
```bash
$ tnsping orcl
```

* TNSNAMES Parameter File
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

* TNS Parameter File
```bash
$ORACLE_HOME/network/admin/sqlnet.ora

# Add oracle dead connection detect(send small packet check every 4 mins.)
SQLNET.EXPIRE_TIME = 4
```

* LISTENER Parameter File
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

* Alert Log
```bash
$ORACLE_BASE/diag/rdbms/orcl/orcl/trace/alert_orcl.log
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

* Failed Start Database (pfile)
```bash
ไม่สามารถ Start Database ได้ ให้ไปสร้างไฟล์ pfile จาก spfile

create pfile from spfile='/u01/app/oracle/product/11.2.0/db_1/dbs/spfileorcl.ora' ;
```

* Failed Start Database (Memory)
```bash
ไม่สามารถ Start Database ได้ เนื่องจาก Memory ไม่พอ ให้ไป Stop Database ใน Instance อื่น เพื่อเรียกคืน Memory หรือไม่งั้นก็ต้องเพิ่ม Physical Memory แล้วทำการ Start Database อีกครั้งหนึ่ง
```

* Failed Import Data Pump (Bigfile Tablespace)
```bash

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
http://shop.oreilly.com/product/9781565925168.do
https://www.scribd.com/document/342208114/57114599-ORACLE-DBA-Activity-Checklist-pdf
https://www.scribd.com/document/17335826/Important-Oracle-Query-Script

## License
Codeinsane license.