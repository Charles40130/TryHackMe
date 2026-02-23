
---

## Nmap Options Reference

| Option | Explanation                                     |
| ------ | ----------------------------------------------- |
| `-sL`  | List scan – lists targets without scanning them |
|        |                                                 |

### Host Discovery

| Option | Explanation                                    |
| ------ | ---------------------------------------------- |
| `-sn`  | Ping scan – host discovery only (no port scan) |

### Port Scanning

| Option      | Explanation                                                            |
| ----------- | ---------------------------------------------------------------------- |
| `-sT`       | TCP connect scan – completes the full three-way handshake              |
| `-sS`       | TCP SYN scan – sends only the first step of the handshake (stealthier) |
| `-sU`       | UDP scan                                                               |
| `-F`        | Fast mode – scans the 100 most common ports                            |
| `-p[range]` | Specifies a range of port numbers. Example: `-p-` scans all ports      |
| `-Pn`       | Treat all hosts as online – scan hosts even if they appear down        |

### Service Detection

| Option | Explanation                                                              |
| ------ | ------------------------------------------------------------------------ |
| `-O`   | OS detection                                                             |
| `-sV`  | Service version detection                                                |
| `-A`   | Enables OS detection, version detection, script scanning, and traceroute |

### Timing

| Option                                                            | Explanation                                                                                    |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `-T<0-5>`                                                         | Timing template – paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), insane (5) |
| `--min-parallelism <numprobes>` / `--max-parallelism <numprobes>` | Minimum and maximum number of parallel probes                                                  |
| `--min-rate <number>` / `--max-rate <number>`                     | Minimum and maximum packet rate (packets/second)                                               |
| `--host-timeout`                                                  | Maximum time to wait for a target host                                                         |

### Real-time Output

| Option | Explanation                            |
| ------ | -------------------------------------- |
| `-v`   | Verbosity level – e.g., `-vv` or `-v4` |
| `-d`   | Debugging level – e.g., `-d` to `-d9`  |

### Report Formats

| Option           | Explanation                 |
| ---------------- | --------------------------- |
| `-oN <filename>` | Normal output               |
| `-oX <filename>` | XML output                  |
| `-oG <filename>` | Grepable output             |
| `-oA <basename>` | Output in all major formats |

---

## Examples

```bash
nmap -sn 192.168.66.0-10
```

👉 Performs a ping scan (host discovery only).

```bash
nmap -sL 192.168.0.1/27
```

👉 Lists targets without scanning them.

---

## Scanning TCP Ports

* **`-sT`**: Attempts to complete the TCP three-way handshake with each target TCP port.
* If Nmap successfully connects to a TCP port, it will then properly close the established connection.

---


`nmap -p 1-1000 10.80.136.114` : scan the n°port of 1 to 1000

Add `-Pn` to the command to force nmap to considere the host as online