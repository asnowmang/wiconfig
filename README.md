#wiconfig
Simplified wifi on OpenBSD

##EXAMPLE

Manually configure a wireless interface

`# sh /etc/wiconfig iwi0`

Automatically scan for wireless networks and, using previous
manual
configurations, configure the wireless interface based on the
strongest
wireless signal (for use with hostname.if(5) files)

```
$ cat /etc/hostname.iwi0
!/bin/sh /etc/wiconfig -q \$if
```

With the above /etc/hostname.iwi0 in place, iwi0 will be
configured
upon startup or whenever /etc/netstart iwi0 is invoked.

wiconfig can also be used in conjunction with apmd.  In the
following
example, upon resume, it'll check the status of the wireless
connection
and, if there is no network connection, it'll automatically scan
for
wireless networks and, using previous manual configurations,
configure
the wireless interface based on the strongest wireless signal.

```
$ cat /etc/apmd/resume
#!/bin/sh
/bin/sh /etc/wiconfig -qs iwi0
```
