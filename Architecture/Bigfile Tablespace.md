# Bigfile Tablespace
โดยปกติ Tablespace จะสร้างเป็น Smallfile Tablespace (SFT) หลาย ๆ ไฟล์
ข้อดี Bigfile Tabelspace
- ง่ายในการจัดการ Tablespace บน Database ขนาดใหญ่
- ง่ายในการจัดการ Datafiles ด้วย Oracle-Managed Files และ

# Table of Content
* Convert Bigfile to Smallfile
* Relocate Datafile

## Convert Bigfile to Smallfile
* Export Data
```bash

```

* Drop Bigfile Tablespace
```bash

```

* Create Smallfile Tablespace
```bash

```

* Import Data
```bash

```

## Relocate Datafile
ในกรณีที่ Tablespace เป็นแบบ Bigfile แล้ว Size Data ใน Mount Point นั้นเต็ม ต้องทำการ Relocate Datafile ไปไว้ที่อื่น
* Offline Tablespace
```bash

```

* Relocate Datafile
```bash

```

## Credit
http://www.dba-oracle.com/t_bigfile_tablespace_tips.htm