![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2022-02-16)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
185.56.80.65|onion.xor.sc|11
5.183.209.217|-|10
89.163.249.244|srv1264.dedicated.server-hosting.expert|10
185.100.87.174|torexit1.flokinet.net|10
45.153.160.2|-|10
80.67.167.81|nosoignons.cust.milkywan.net|10
116.105.212.31|-|9
5.2.69.50|-|9
171.25.193.77|tor-exit1-readme.dfri.se|9
171.25.193.78|tor-exit4-readme.dfri.se|9
81.17.18.60|block1-che.interlayer.co.uk|9
185.220.100.255|tor-exit-4.zbau.f3netze.de|9
185.100.87.72|iclnm.worlpeed.net|9
171.25.193.25|tor-exit5-readme.dfri.se|9
5.2.73.169|-|9
213.202.216.189|h176.helix.dedi.server-hosting.expert|9
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|9
179.43.139.10|-|9
185.129.61.6|tor-project-exit6.dotsrc.org|9
45.153.160.136|-|9
37.123.163.58|h-37-123-163-58.a785.priv.bahnhof.se|9
162.247.74.204|billsf.tor-exit.calyxinstitute.org|8
107.189.10.237|tor-exit-readme.donpablo.me|8
89.185.85.100|85-100.bridge-connect.ru|8
89.234.157.254|marylou.nos-oignons.net|8
89.163.249.192|srv1116.dedicated.server-hosting.expert|8
185.36.81.95|-|8
185.220.102.244|185-220-102-244.torservers.net|8
185.220.102.247|185-220-102-247.torservers.net|8
185.220.102.240|185-220-102-240.torservers.net|8
185.220.102.241|185-220-102-241.torservers.net|8
185.220.102.243|185-220-102-243.torservers.net|8
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|8
185.220.102.249|tor-exit-relay-3.anonymizing-proxy.digitalcourage.de|8
185.220.101.4|berlin01.tor-exit.artikel10.org|8
185.220.101.1|berlin01.tor-exit.artikel10.org|8
185.42.170.203|exit01.tor.anduin.net|8
23.154.177.21|-|8
185.220.100.254|tor-exit-3.zbau.f3netze.de|8
185.220.100.253|tor-exit-2.zbau.f3netze.de|8
185.220.100.252|tor-exit-1.zbau.f3netze.de|8
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|8
185.220.102.4|communityexit.torservers.net|8
185.220.102.8|185-220-102-8.torservers.net|8
45.155.204.161|-|8
23.154.177.19|-|8
45.153.160.140|-|8
185.220.103.7|anatkamm.tor-exit.calyxinstitute.org|8
116.110.3.253|-|8
185.100.86.74|-|8
171.25.193.20|tor-exit0-readme.dfri.se|8
185.220.102.254|tor-exit-relay-8.anonymizing-proxy.digitalcourage.de|8
185.220.102.251|tor-exit-relay-5.anonymizing-proxy.digitalcourage.de|8
185.220.102.250|tor-exit-relay-4.anonymizing-proxy.digitalcourage.de|8
204.8.156.142|cs-tor.bu.edu|8
45.9.20.25|-|8
23.154.177.6|-|8
23.154.177.5|-|8
5.2.70.140|nl2.b.illya.club|8
62.102.148.69|-|8
89.185.85.253|85-253.bridge-connect.ru|8
45.154.168.39|ip.39.168.154.45.as208196.net|8
185.129.61.2|tor-project-exit2.dotsrc.org|8
45.153.160.133|-|8
45.153.160.130|-|8
45.153.160.135|-|8
45.153.160.134|-|8
45.153.160.139|-|8
46.182.21.248|tor-exit-relay.anonymizing-proxy.digitalcourage.de|8
185.220.100.243|tor-exit-16.zbau.f3netze.de|8
192.42.116.27|this-is-a-tor-exit-node-hviv127.hviv.nl|8
185.100.87.202|-|8
179.43.187.173|-|7
89.163.252.230|ca262.calcit.dedicated.server-hosting.expert|7
128.31.0.13|tor-exit.csail.mit.edu|7
218.92.0.221|-|7
80.82.77.33|sky.census.shodan.io|7
122.194.229.37|-|7
122.194.229.38|-|7
162.247.74.201|kunstler.tor-exit.calyxinstitute.org|7
45.61.187.112|mail3.wedifferentiate.com|7
91.250.242.12|-|7
185.107.47.215|tor-exit.r1.ci.ax|7
112.85.42.128|-|7
61.177.172.154|-|7
185.220.102.242|185-220-102-242.torservers.net|7
162.247.74.74|-|7
112.85.42.119|-|7
112.85.42.15|-|7
185.220.103.5|chelseamanning.tor-exit.calyxinstitute.org|7
198.98.49.20|-|7
185.107.47.171|tor-exit.r2.ci.ax|7
45.154.255.147|cust-147.keff.org|7
198.98.51.76|-|7
185.220.101.40|tor-exit-40.for-privacy.net|7
185.220.101.42|tor-exit-42.for-privacy.net|7
112.85.42.89|-|7
112.85.42.87|-|7
80.82.77.139|dojo.census.shodan.io|7
23.154.177.7|-|7
185.100.87.133|-|7
193.169.252.71|-|7
185.254.75.32|185.254.75.32.dus.mullvad.net|7
81.17.18.61|block1-che.interlayer.co.uk|7
81.17.18.62|block1-che.interlayer.co.uk|7
209.141.54.195|tor1.friendlyexitnode.com|7
193.218.118.158|158.118.218.193.urdn.com.ua|7
45.153.160.129|-|7
61.177.172.89|-|7
195.254.135.76|-|7
185.165.168.229|-|7
192.42.116.14|this-is-a-tor-exit-node-hviv114.hviv.nl|7
192.42.116.15|this-is-a-tor-exit-node-hviv115.hviv.nl|7
166.70.207.2|this.is.a.tor.node.xmission.com|7
116.105.174.1|-|7
185.130.44.108|tor-exit-se1.privex.cc|7
5.2.72.168|-|7
116.105.216.128|-|7
118.26.65.165|-|7
112.85.42.28|-|7
46.19.139.18|-|7
193.169.255.199|-|7
122.194.229.40|-|7
122.194.229.45|-|7
162.247.74.27|-|7
93.174.95.106|battery.census.shodan.io|7
112.85.42.71|-|7
162.247.74.216|-|7
162.247.74.217|-|7
112.85.42.88|-|7
107.189.29.207|-|7
91.219.236.228|441061389-dedicated.serverastra.com|7
118.186.201.132|-|7
185.220.102.252|tor-exit-relay-6.anonymizing-proxy.digitalcourage.de|7
64.113.32.29|tor.t-3.net|7
209.141.55.96|platinumhost.xyz|7
112.85.42.229|-|7
112.85.42.227|-|7
23.154.177.2|-|7
23.154.177.3|-|7
112.85.42.124|-|7
185.165.171.175|-|7
45.129.56.200|-|7
185.165.169.18|-|7
89.163.252.30|srv1016.dedicated.server-hosting.expert|7
185.129.62.62|tor01.zencurity.dk|7
209.141.58.146|tor-exit.riverside.rocks|7
45.153.160.132|-|7
45.153.160.131|-|7
45.153.160.137|-|7
45.153.160.138|-|7
185.220.100.240|tor-exit-13.zbau.f3netze.de|7
185.220.101.17|berlin01.tor-exit.artikel10.org|7
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|7
192.42.116.24|this-is-a-tor-exit-node-hviv124.hviv.nl|7
45.33.65.249|45-33-65-249.ip.linodeusercontent.com|7
122.194.229.54|-|7
5.2.75.253|tor-exit-rainer.cfgdhb.de|7
112.85.42.73|-|7
112.85.42.74|-|7
198.98.51.189|tor.teitel.net|7
179.43.187.95|-|7
185.220.103.115|-|7
46.166.139.111|-|7
