# Oracle Script
Documentation for Oracle Script
```bash

```

# Table of Content
* Check Path Script
* Run SQL Script
* Cron Job

## Check Path Script

* Locate
```
locate [option] [filename]
 -b --basename  :use patterns is search by match only
 -r --regexp    :no use patterns is search by relular expression
```

* Print Working Directory
```
pwd [option]
 -L --logical   :absolute path or symbolic links
 -P --physical  :relative path or hard links
```

## Run SQL Script

* Login SQL*Plus
```
$ sqlplus / as sysdba
```

* Run Script in SQL*Plus
```
SQL> @/home/oracle/script.sql
```

## License
Codeinsane license.