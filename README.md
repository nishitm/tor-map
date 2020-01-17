# Tor-map

This port scanner was orginally made by [Nishit Majithia](https://github.com/nishitm) for fun.

It was modifed to work over **Tor** for anonymous and hidden service scanning.

### Dependencies
Tor-map is a python script that requries the **socks** module and a running Tor deamon on localhost.

Tor-map is built to support **python3**.

### Usage:
`./tor-map [-h] -H HOSTS [-p PORTS] [-t TIMEOUT] [--clearnet] [--torport TORPORT]`


`-H` option can be used to specify hosts, but it is assumed by default.

Multiple hosts can be specified using a comma (ex. `./tor-map -H 1.1.1.1,google.com,facebookcorewwwi.onion -p 80`).

Tor-map supports IP address ranges as well (ex. `./tor-map 192.168.1.0/24 -p 22`).

**For private addresses, Tor is _not_ used, but a _direct_ connection is established instead.**

Ports can be specified as a range (ex. `./tor-map google.com -p 20-30`),separated with a comma (ex. `./tor-map 1.1.1.1 -p 25,53,80`) or both.

Ports in a range are scanned including the ends of an interval (ex. in a range "20-30" both port 20 and 30 are scanned).

### Examples

`./tor-map -H 1.1.1.1 -p 53,80`

Scans ports 53 and 80 on 1.1.1.1

`./tor-map -H facebookcorewwwi.onion -p 80`

Scan port 80 on facebookcorewwwi.onion

`./tor-map -H 192.168.0.1 -p 0-1024 --clearnet`

Scan ports from 0 to 1024 on 192.168.0.1 without routing traffic through Tor.

`./tor-map 192.168.1.0/24,google.com -p 80`

Scan the whole 192.168.1.0/24 range for an open port 80 without Tor and goole.com with Tor.

`./tor-map 8.8.8.8/31 -p 53`

Scan the 8.8.8.8/31 range for an open port 53 with Tor.

### License
**GPLv3+**: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>

This is *free* software: you are free to change and redistribute it.
