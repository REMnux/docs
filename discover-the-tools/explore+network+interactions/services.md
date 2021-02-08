---
description: Explore Network Interactions
---

# Services

## fakedns

Respond to DNS queries with the specified IP address.

**Website**: [https://github.com/SocialExploits/fakedns/blob/main/fakedns.py](https://github.com/SocialExploits/fakedns/blob/main/fakedns.py)  
**Author**: Mike Murr: mike@socialexploits.com, [https://socialexploits.com](https://socialexploits.com)  
**License**: Apache License 2.0  
**Notes**: Use the `-h` parameter to display usage and help details.  
**State File**: [remnux.tools.fakedns](https://github.com/REMnux/salt-states/blob/master/remnux/tools/fakedns.sls)

## fakemail

Intercept and examine SMTP email activity with this fake SMTP server. Available in the REMnux distro based on Ubuntu 20.04 \(Focal\); not available on Ubuntu 18.04 \(Bionic\).

**Website**: [https://hg.sr.ht/~olly/fakemail](https://hg.sr.ht/~olly/fakemail)  
**Author**: Oliver Cope  
**License**: Apache License 2.0: [https://hg.sr.ht/~olly/fakemail/browse/LICENSE.txt?rev=default](https://hg.sr.ht/~olly/fakemail/browse/LICENSE.txt?rev=default)  
**State File**: [remnux.python3-packages.fakemail](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/fakemail.sls)

## accept-all-ips

Accept connections to all IPv4 and IPv6 addresses and redirect it to the corresponding local port.

**Website**: [https://github.com/REMnux/distro/blob/master/files/accept-all-ips](https://github.com/REMnux/distro/blob/master/files/accept-all-ips)  
**Author**: Lenny Zeltser, with input from the community  
**License**: GNU General Public License \(GPL\) v3+  
**Notes**: accept-all-ips &lt;start\|stop&gt;  
**State File**: [remnux.scripts.accept-all-ips](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/accept-all-ips.sls)

## netcat

Read and write data across network connections.

**Website**: [https://nc110.sourceforge.io/](https://nc110.sourceforge.io/)  
**Author**: Hobbit, Mike Frysinger, a3alex, Anatoly Techtonik  
**License**: Public Domain  
**Notes**: nc  
**State File**: [remnux.packages.netcat](https://github.com/REMnux/salt-states/blob/master/remnux/packages/netcat.sls)

## Nginx

Web server

**Website**: [https://nginx.org](https://nginx.org)  
**Author**: Igor Sysoev, Nginx Inc.  
**License**: Free, custom license: [https://nginx.org/LICENSE](https://nginx.org/LICENSE)  
**Notes**: The webroot directory is /var/www/html. Control the daemon using: httpd &lt;start\|stop\|status\|restart&gt;.  
**State File**: [remnux.packages.nginx](https://github.com/REMnux/salt-states/blob/master/remnux/packages/nginx.sls)

## inspircd 3

Examine IRC activity with this IRC server.

**Website**: [https://www.inspircd.org/](https://www.inspircd.org/)  
**Author**: InspIRCd Development Team  
**License**: GNU General Public License \(GPL\) v2: [https://docs.inspircd.org/license/](https://docs.inspircd.org/license/)  
**State File**: [remnux.packages.inspircd](https://github.com/REMnux/salt-states/blob/master/remnux/packages/inspircd.sls)

## INetSim

Emulate common network services and interact with malware.

**Website**: [https://www.inetsim.org/](https://www.inetsim.org/)  
**Author**: Thomas Hungenberg, Matthias Eckert  
**License**: GNU General Public License \(GPL\) v3  
**Notes**: inetsim  
**State File**: [remnux.packages.inetsim](https://github.com/REMnux/salt-states/blob/master/remnux/packages/inetsim.sls)

## FakeNet-NG

Emulate common network services and interact with malware.

**Website**: [https://github.com/fireeye/flare-fakenet-ng](https://github.com/fireeye/flare-fakenet-ng)  
**Author**: FireEye Inc, Peter Kacherginsky, Michael Bailey: [https://github.com/fireeye/flare-fakenet-ng/blob/master/AUTHORS](https://github.com/fireeye/flare-fakenet-ng/blob/master/AUTHORS)  
**License**: Apache License 2.0: [https://github.com/fireeye/flare-fakenet-ng/blob/master/LICENSE.txt](https://github.com/fireeye/flare-fakenet-ng/blob/master/LICENSE.txt)  
**Notes**: Run the tool using `sudo fakenet`. First, edit `/usr/lib/python2.7/dist-packages/fakenet/configs/default.ini`, changing the `LinuxRestrictInterface` parameter to your Ethernet network interface name, such as `ens33`.  
**State File**: [remnux.packages.fakenet-ng](https://github.com/REMnux/salt-states/blob/master/remnux/packages/fakenet-ng.sls)

