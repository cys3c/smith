# smith
A client/server style agent meant for testing connectivity to and from a machine on a network.

```bash
$: smith -h
usage: smith [-h] ping, listen ...

positional arguments:
  ping, listen

optional arguments:
  -h, --help    show this help message and exit
```
---
## ping
```bash
$: smith ping -h

usage: 
  Initiate a port-specific ping against a listening agent

positional arguments:
  port                  The port the remote agent is listening on
  destination           IPv4 address of the server the remote agent is
                        listening on
  {TCP,UDP,REST}        Protocol to use to contact the remote agent. TCP and
                        UDP use raw sockets which will bypass IPTABLES rules.

optional arguments:
  -h, --help            show this help message and exit
  -t TIMEOUT, --timeout TIMEOUT
                        Seconds to wait for response from server before giving
                        up. Zero means 'wait forever'
```
### Example
```bash
$: smith ping 12345 127.0.0.1 REST --timeout 10
```
---

## listen
```bash
$: smith listen -h
usage: 
 Server-side: listen for incoming ping requests from remote client.

positional arguments:
  port            The port the remote client is pinging
  {TCP,UDP,REST}  Protocol to use to contact the remote agent.TCP and UDP use
                  raw sockets which will bypass IPTABLES rules.

optional arguments:
  -h, --help      show this help message and exit
```

### Example
```bash
$: smith ping 12345 127.0.0.1 REST --timeout 10
```
