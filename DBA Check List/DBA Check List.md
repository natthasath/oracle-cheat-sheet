# DBA Check List
Description job all task of Database Administrator (DBA) for check list seperate collection by risk level. You should use monitoring tools ex. (Oracle Enterprise Manager, Dell Foglight) but other job you should monitoring and managing yourself. It's include health check report every month.

# Table of Content

* Oracle DBA
* Daily DBA Checklist
* Daily Night DBA Checklist
* Weekly DBA Checklist
* Weekly Tuning DBA Checklist
* Monthly DBA Checklist
* Quarterly DBA Checklist
* One Time Activity DBA Checklist

## Oracle DBA
* Installation of Oracle 11g on linux/Solaris/Windows
* Database Architecture - Physical/Logical
* Instance - SGA/PGA/BG Process
* Database Creation
* Tablespace Management
* Usrers/Roles/Privileges/Profiles
* Storage Parameters
* Undo Management
* Managing Redolog files
* Managing control files
* Archived Redolog files
* Oracle Managed Files
* Auditing
* Oracle Networking - listener.ora/tnsnames.ora/dblinks/global names/Materialized views
* Managing Exports & Imports
* Datapump / TTS
* Cold Backup / Hot Backup (8 Scenarios)
* Database Cloning
* RMAN
* Partitioning
* SQL Loader
* Performance Tuning - server/Instance/Object/SQL Tuning .. AWR/ADDM .. TKPROF/EXPLAIN PLAN
* Flashback Technology
* ASM
* Dataguard - scenarios
* RAC
* Applying CPU Patch
* Upgradation from 9i to 10g / 10g to 11g
 
## Daily DBA Checklist
* Health check of the Database Instance and Listener.
* Monitor Alert log file and/or check Alert log in regular interval to solve the ORA errors.
* Check any session blocking the other session and oracle locks. Clear locks
* Check long running UNIX process
* Ensure that there are no DBMS_JOBS with the status of failed or broken. Also last refresh times of all running jobs should be current.
* Check all CRONTAB house keeping script logs
* Daily Tablespace utilization and growth.
* Rebuilding of Indexes, if bulk load of data is inserted.
* Check the temporary tablespace/files.
* Check locked and expired user in database and unlock/reset/inform to business users. Monitor user account GRACE period.
* Check the UNDO tablespace and retention.
* Monitor the Unix /tmp and /var location
* Monitor the UTL_FILE location.
* Monitor all Database file system or drive.
* Monitor Archive Log location.
* Verify success of database archiving to tape
* Monitoring Backups.
* Monitoring the log files, backups, database space usage and the use of system resources.
* Monitoring Production Database Performance
* Find high CPU/Memory/Physical IO consuming processes and trace the SQL/From/Report running behind the database and update to application team/users.
* Check OEM Agent is running Or not in each node.
* Verify DBSNMP is running
* Verify success of database backup
* Daily RMAN(Incremental & Cumulative)/Data Pump export backups after business hours.
* User Management. User Profile monitoring.
* Check Invalid objects and recompile.
* Check and monitor audit log or table for new audit entry.
* Monitor daily failed login attempt in database and update to respective end uses.
* Backup your CRONTAB or Windows job scheduler
* Most Important - read DBA manuals for one hour daily.
* Most Important - Check your oracle license and do not run/execute/create anything beyond the oracle license policy.

## Daily Night DBA Checklist
* Look for objects that break rules (Check for Huge NEXT_EXTENT or MAX_EXTENT)
* Check the objects reaching to it’s Max extents
* Note, All tables should have unique primary keys, so check missing/disabled PK and
* Check for Block corruption

## Weekly DBA Checklist
* Look for objects that break rules (Check for Huge NEXT_EXTENT or MAX_EXTENT)
* Check the objects reaching to it’s Max extents
* Note, All tables should have unique primary keys, so check missing/disabled PK and
* Check for Block corruption

## Weekly Tuning DBA Checklist
* Look for objects that break rules (Check for Huge NEXT_EXTENT or MAX_EXTENT)
* Check the objects reaching to it’s Max extents
* Note, All tables should have unique primary keys, so check missing/disabled PK and
* Check for Block corruption

## Monthly DBA Checklist
* Index Rebuild.
* Tablespace reorganization.
* Bounce critical database once a month (If no cold backup configured)
* Look for Harmful Growth Rates
* Review database file activity.  Compare to past output to identify trends that could lead to possible contention.
* Investigate fragmentation (e.g. row chaining, etc.).
* Check location of data file also check auto extendable or not
* Check default tablespace & temporary tablespace of each user
* Check the Extents of each object and compare if any object extent are overridden which is define at tablespace level
* Tablespace need coalescing
* Check the overall database statistics
* Trend analysis of objects with tablespace, last analysed, no. of Rows, Growth in days & growth in KB

## Quarterly DBA Checklist
* Patching
* Database Reorganization
* Check the quota of non-system tables in system tablespace.
* Bounce most critical database once a month (If no cold backup configured)
* Review common Oracle tuning points such as cache hit ratio, latch contention, and other points dealing with memory management

## One Time Activity DBA Checklist
* Database user creation with required privileges
* Make the portal of Oracle Predefined error with possible solution.
* Check database start-up time(if not 24X7)
* Check location of control file
* Check location of log file
* Prepare the Backup strategy and test all the recovery scenario

## Credit
http://durga-kar.blogspot.com/2014/04/dba-checklist-activities-of-oracle-dba.html