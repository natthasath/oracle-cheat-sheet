# Oracle Linux
Documentation for Oracle DBA beginner
```bash

```

# Table of Content

* Download
* System Requirement
* Install
* Configuration
* Command Cheat Sheet

## Download

Oracle Linux เป็น Distribution หนึ่งของ Linux based on Red Hat ที่สามารถ Download ได้ฟรี ปัจจุบันเป็น Oracle Linux Version 7 แล้ว สามารถใช้งานร่วมกับ Docker, Vagrant
หรือจะโหลดเป็น Hands-On Labs สามารถ Donload ผ่านทาง [Oracle Software Delivery Cloud](https://edelivery.oracle.com/osdc/faces/SoftwareDelivery)
โดยเลือก Version และสถาปัตยกรรม 32-bit หรือ 64-bit ให้ตรงกับที่เราต้องการ ใน LAB นี้จะติดตั้ง Oracle Linux Version 6.8

![](/Images/01.png)

## System Requirement

* Memory Minimum 1 GB and Maximum 64 GB
* Disk Space Mnimum 1 GB and Maximum 4 TB

## Install

Host File (/etc/hosts)
```bash
127.0.0.1       localhost.localdomain  localhost
192.168.0.181   ol6-112.localdomain    ol6-112
```

Oracle Installation Prerequisites
```bash
yum install oracle-rdbms-server-11gR2-preinstall
yum update
```

Set Password Oracle User
```bash
passwd oracle
```

Set SELinux (/etc/selinux/config)
```bash
SELINUX=permissive
```

Create Directory
```bash
mkdir -p /u01/app/oracle/product/11.2.0/db_1
chown -R oracle:oinstall /u01
chmod -R 775 /u01
```

Change Root to Oracle User
```bash
su oracle
```

Bash Profile (.bash_profile)
```
# Oracle Settings
TMP=/tmp; export TMP
TMPDIR=$TMP; export TMPDIR

ORACLE_HOSTNAME=ol6-112.localdomain; export ORACLE_HOSTNAME
ORACLE_UNQNAME=DB11G; export ORACLE_UNQNAME
ORACLE_BASE=/u01/app/oracle; export ORACLE_BASE
ORACLE_HOME=$ORACLE_BASE/product/11.2.0/db_1; export ORACLE_HOME
ORACLE_SID=DB11G; export ORACLE_SID

PATH=/usr/sbin:$PATH; export PATH
PATH=$ORACLE_HOME/bin:$PATH; export PATH

LD_LIBRARY_PATH=$ORACLE_HOME/lib:/lib:/usr/lib; export LD_LIBRARY_PATH
CLASSPATH=$ORACLE_HOME/jlib:$ORACLE_HOME/rdbms/jlib; export CLASSPATH
```

## Command Cheat Sheet

* Option short use (-) and long use (--)

Find Port
```bash
netstat -anp | grep port_number
```

Create Directory
```bash
mkdir [option] [name]
 -m --mode		set permission file mode (chmod)
 -p --parent		make parent directory (relative and absolute path)
 -v --verbose		print message
 -z --context=CTX	set SELinux security
```

Package
```bash
yum update
yum install
yum remove
yum history
yum clean
yum list
```

Service
```bash
service [name] start
service [name] stop
service [name] status
```











