#CNTLM-GSS

This is [Cntlm](http://cntlm.sourceforge.net/) **with Kerberos patch applied**.

Works on a Ubuntu 12.04 box, at least for me.

## Dependency

* [Kerberos](http://web.mit.edu/kerberos/)
* [debhelper](http://manpages.ubuntu.com/manpages/wily/man7/debhelper.7.html) - otherwise fail on command `dh_testdir`
* [libkrb5-dev](http://packages.ubuntu.com/ru/trusty/libkrb5-dev) - otherwise fail on `#include <gssapi/gssapi.h>`

If Kerberos is compiled to a different location, say, $HOME/usr, compile Cntlm with

`./configure --enable-kerberos`

`export LIBRARY_PATH=$HOME/usr/lib`

`export C_INCLUDE_PATH=$HOME/usr/include`

`make` or `make deb` or mode details on [README](README)

Finally, run it, try `cntlm --help` or `cntlm -v` and fix whatever it complains.

I have only the following lines in my ctnlm.conf file:

```
Username	
Domain		
Password	
Proxy		proxy.server.domain.com:3128
NoProxy		localhost, 127.0.0.*, 10.*, 192.168.*
Listen		3128
```

The username, domain and password are all unset.

I could start it with `/home/me/usr/opt/cntlm-0.92.3/cntlm -a gss -c /home/me/usr/opt/cntlm-0.92.3/cntlm.conf` .
