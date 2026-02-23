
- capture packets and save them to a file
- set filters on captured packets
- control how captured packets are displayed

`ip a s` or `ip address show` list the available network interfaces

`sudo tcpdump -i ens5 -c 5 -n`  : capture 5 packets on a specific interface
- `i ens5` : listen the trafic on the interface ens5
- `-c 5` : indicate that we want to capture 5 packets and stop
- `-n` : Don't resolve ip addresses ( ip  stay en numeric format)

| Command                                      | Explanation                                                           |
| -------------------------------------------- | --------------------------------------------------------------------- |
| `tcpdump -i INTERFACE`                       | Captures packets on a specific network interface                      |
| `tcpdump -w FILE`                            | Writes captured packets to a file                                     |
| `tcpdump -r FILE`                            | Reads captured packets from a file                                    |
| `tcpdump -c COUNT`                           | Captures a specific number of packets                                 |
| `tcpdump -n`                                 | Don’t resolve IP addresses                                            |
| `tcpdump -nn`                                | Don’t resolve IP addresses and don’t resolve protocol numbers         |
| `tcpdump -v`                                 | Verbose display; verbosity can be increased with `-vv` and `-vvv`     |
| `tcpdump host IP` or `tcpdump host HOSTNAME` | Filters packets by IP address or hostname                             |
| `tcpdump src host IP` or                     | Filters packets by a specific source host                             |
| `tcpdump dst host IP`                        | Filters packets by a specific destination host                        |
| `tcpdump port PORT_NUMBER`                   | Filters packets by port number                                        |
| `tcpdump src port PORT_NUMBER`               | Filters packets by the specified source port number                   |
| `tcpdump dst port PORT_NUMBER`               | Filters packets by the specified destination port number              |
| `tcpdump PROTOCOL`                           | Filters packets by protocol; examples include `ip`, `ip6`, and `icmp` |

`sudo tcpdump -r traffic.pcap port 53` : show the dns trafic on the file traffic.pcap


`sudo tcpdump -r traffic.pcap "tcp[tcpflags] == tcp-rst" | wc -l`:
show the packets which have only the tcp reset ( RST) flag set and count them

***

| Command       | Explanation                                        |
| ------------- | -------------------------------------------------- |
| `tcpdump -q`  | Quick and quite: brief packet information          |
| `tcpdump -e`  | Include MAC addresses                              |
| `tcpdump -A`  | Print packets as ASCII encoding                    |
| `tcpdump -xx` | Display packets in hexadecimal format              |
| `tcpdump -X`  | Show packets in both hexadecimal and ASCII formats |