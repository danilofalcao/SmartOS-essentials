# SmartOS

# Author: dfs @ freenode

# pkgin

```
cd /
curl -k http://pkgsrc.joyent.com/packages/SmartOS/bootstrap/bootstrap-2016Q2-x86_64.tar.gz | gzcat | tar -xf -
pkg_admin rebuild
pkgin -y up
```

# rc.local

```
svccfg import /opt/custom/smf/setup.xml
svcadm enable svc:/smartos/setup:default
```

# ipnat

```
map e1000g0 172.16.0.0/12 -> 0/32

/usr/sbin/ipf -E -Fa -v -f /etc/ipf/ipf.conf
/usr/sbin/ipnat -C -v -f /etc/ipf/ipnat.conf
```

# services

```
svcs -a

svcadm restart nginx
```

# logs

```
svcs -l

svcs -L svc:/network/ipfilter:default
```

# ntpd [ /etc/inet/ntp.conf ]

```
interface ignore wildcard
interface listen 127.0.0.1
interface listen ::1
```
