# Oracle Docker
Documentation for Oracle Docker
```bash

```

## Error Build Image
* Error Message
```bash
ERROR: Get https://registry-1.docker.io/v2/: dial tcp: lookup registry-1.docker.io on [::1]:53: read udp [::1]:59801->[::1]:53: read: connection refused
```

* Solve Problem
```bash
reinstall docker
```

## Error Devicemapper
* Error Message
```bash
WARNING: devicemapper: usage of loopback devices is strongly discouraged for production use.
```

* Solve Problem
```bash
# lvcreate -n docker-data -L 100G /dev/my-vg
# lvcreate -n docker-metadata -L1G /dev/my-vg
# vi /etc/sysconfig/docker-storage
DOCKER_STORAGE_OPTIONS=-s devicemapper --storage-opt dm.datadev=/dev/my-vg/docker-data --storage-opt dm.metadatadev=/dev/my-vg/docker-metadata

http://www.projectatomic.io/blog/2015/06/notes-on-fedora-centos-and-docker-storage-drivers/
```

## Error Kill Process
* Error Message
```bash
rm: cannot remove Device or resource busy
```

* Solve Problem
```bash
# lsof +D /Path
# kill -9 /PID

# Service docker stop
# rm -rf /var/lib/docker
```

## Credit
http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index.html
http://www.oracle.com/technetwork/database/enterprise-edition/downloads/oracle12c-linux-12201-3608234.html
https://sqlmaria.com/2017/04/27/oracle-database-12c-now-available-on-docker/

## License
Codeinsane license.