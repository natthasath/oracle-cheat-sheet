# Oracle RMAN
Recovery Manager (RMAN) is an Oracle Database client that performs backup and recovery and automates administration of your backup strategies

## Check Archive Log
```bash
SQL> archive log list
```

## Open Archive Log
```bash
SQL> startup mount ;
SQL> select log_mode from v$database ;
SQL> alter database archivelog ;
SQL> alter database open ;
```

## Check Recovery Size and Destination
```bash
SQL> show parameter db_recovery ;
SQL> select * from V$RECOVERY_FILE_DEST ;
SQL> select * FROM V$RECOVERY_AREA_USAGE ;
SQL> alter system set db_recovery_file_dest_size=4070572032 scope=both ;
SQL> alter system set db_recovery_file_dest_size=8G ;
```

## Start RMAN
```bash
$ rman
RMAN> connect target /
```

## Start RMAN with Target
```bash
$ rman target /
$ rman target / nocatelog
```

## Show Configuration
```bash
RMAN> show all ;

using target database control file instead of recovery catalog
RMAN configuration parameters for database with db_unique_name MEIS are:
CONFIGURE RETENTION POLICY TO RECOVERY WINDOW OF 4 DAYS;
CONFIGURE BACKUP OPTIMIZATION ON;
CONFIGURE DEFAULT DEVICE TYPE TO DISK;
CONFIGURE CONTROLFILE AUTOBACKUP OFF;
CONFIGURE CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE DISK TO '%F'; # default
CONFIGURE DEVICE TYPE DISK PARALLELISM 8 BACKUP TYPE TO BACKUPSET;
CONFIGURE DATAFILE BACKUP COPIES FOR DEVICE TYPE DISK TO 1; # default
CONFIGURE ARCHIVELOG BACKUP COPIES FOR DEVICE TYPE DISK TO 1; # default
CONFIGURE MAXSETSIZE TO UNLIMITED; # default
CONFIGURE ENCRYPTION FOR DATABASE OFF; # default
CONFIGURE ENCRYPTION ALGORITHM 'AES128'; # default
CONFIGURE COMPRESSION ALGORITHM 'MEDIUM' AS OF RELEASE 'DEFAULT' OPTIMIZE FOR LOAD TRUE;
CONFIGURE ARCHIVELOG DELETION POLICY TO NONE; # default
CONFIGURE SNAPSHOT CONTROLFILE NAME TO '/oracle/products/11.2.0.2.0/db_1/dbs/snapcf_MEIS.f'; # default
```

## Backup Archivelog Mode
```bash
RMAN> backup database plus archivelog ;
```

## Backup no Archivelog Mode
```bash
RMAN> backup database ;
RMAN> backup as copy database ;
```

## List Backup Summary
```bash
RMAN> list backup summary ;
```

## Fix Error
```bash
ORA-19809: limit exceeded for recovery files
ORA-19804: cannot reclaim 52428800 bytes disk space from 4070572032 limit
http://marcel.vandewaters.nl/oracle/database-oracle/ora-19809-limit-exceeded-for-recovery-files
```

## Credit
https://docs.oracle.com/cd/E11882_01/backup.112/e10642/rcmquick.htm#BRADV89350

http://www.scsi.co.th/home/15/index.php?option=com_content&view=article&id=71:oracle----archive-log&catid=36:database&Itemid=63

## License
Codeinsane license.


## RMAN History Command
```bash
SQL> select sid, recid, output from v$rman_output order by recid
```

## RMAN Session and Status
```bash
SQL> select session_key, INPUT_TYPE, STATUS, to_char(START_TIME,'mm/dd/yy hh24:mi') start_time, to_char(END_TIME,'mm/dd/yy hh24:mi') end_time, elapsed_seconds/3600 hrs from V$RMAN_BACKUP_JOB_DETAILS order by session_key;
```
