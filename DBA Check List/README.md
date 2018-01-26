# DBA Check List
Description
```bash

```

## Oracle Database Enterprise Edition 11GR2
https://FQDN:5500/em

## Check Disk
df -h

## Check Listener
lsnrctl status

## Check Enterprise Manager
emctl status dbconsole

## Environment
export ORACLE_HOME
export ORACLE_SID=XE
export ORACLE_PATH

## SQL Plus
sqlplus /nolog
SQL> connect / as sysdba
SQL> select user, instance_name, status from v$instance