***
`namp -sn 192.168.66.0-10` :scan
`-sn` : ping scan

`nmap 192.168.0.1/27 -sL` 

Scanning TCP Ports
* `sT` :tries to complete the TCP three-way-handshake with every target TCP ports
* if Nmap connects to a tcp port , it will tear down the etablish connection



| Option      | Explanation                                                   |
| ----------- | ------------------------------------------------------------- |
| `-sT`       | TCP connect scan – complete three-way handshake               |
| `-sS`       | TCP SYN – only first step of the three-way handshake          |
| `-sU`       | UDP scan                                                      |
| `-F`        | Fast mode – scans the 100 most common ports                   |
| `-p[range]` | Specifies a range of port numbers – `-p-` scans all the ports |