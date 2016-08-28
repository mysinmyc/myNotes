TIPS
====



## Tags

\#ssh,\#X11,\#tunnel,\#/bin/sh,\#dash



## Lightweight encryption to increase ssh x11 tunnels speed

`ssh -X -c blowfish-cbc,arcfuour {...} `



## Recent Ubuntu /bin/sh is dash

In case of issues with script that uses #!/bin/sh in recent version of ubuntu, the default shell (symbolic lync /bin/sh) has been changed to dash
