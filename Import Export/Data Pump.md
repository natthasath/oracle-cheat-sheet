# Oracle Data Pump
Data pump is a server based technology which enables very high speed import and export data (expdp / impdp)
```bash

```

## Privileged users
* Export and import database objects owned by others
* Export and import nonschema-based objects such as tablespace and schema definitions, system privilege grants, resource plans, and so forth
* Attach to, monitor, and control Data Pump jobs initiated by others
* Perform remapping operations on database datafiles
* Perform remapping operations on schemas other than their own

## Table Export/Import
```bash
expdp scott/tiger@DB11G tables=EMP,DEPT directory=TEST_DIR dumpfile=EMP_DEPT.dmp logfile=expdpEMP_DEPT.log
impdp scott/tiger@DB11G tables=EMP,DEPT directory=TEST_DIR dumpfile=EMP_DEPT.dmp logfile=impdpEMP_DEPT.log
```

## Schema Export/Import
```bash
expdp scott/tiger@db10g schemas=SCOTT directory=TEST_DIR dumpfile=SCOTT.dmp logfile=expdpSCOTT.log
impdp scott/tiger@db10g schemas=SCOTT directory=TEST_DIR dumpfile=SCOTT.dmp logfile=impdpSCOTT.log
```

## Database Export/Import
```bash
expdp system/password@db10g full=Y directory=TEST_DIR dumpfile=DB10G.dmp logfile=expdpDB10G.log
impdp system/password@db10g full=Y directory=TEST_DIR dumpfile=DB10G.dmp logfile=impdpDB10G.log
```

## Credit
