`netstat` and similar command-line tools can help you monitor network connections, open files, and socket states on your system. While `netstat` is often used for network connections, there are other tools like `lsof` for listing open files.

Let's break down `netstat` and `lsof`, focusing on macOS usage, including basic commands and flags.

---

### 1. **`netstat`** (Network Statistics)

`netstat` is used to display network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.

#### **Basic Usage**
```bash
netstat [options]
```

#### **Common Options for macOS:**
1. **List all network connections:**
   ```bash
   netstat -a
   ```
   Displays all active connections (both listening and established).

2. **Show active TCP/UDP connections:**
   ```bash
   netstat -an
   ```
   Displays active TCP and UDP connections in numeric format (without resolving hostnames).

3. **Display routing table:**
   ```bash
   netstat -r
   ```
   Shows the routing table of your system.

4. **Show network interface statistics:**
   ```bash
   netstat -i
   ```
   Provides statistics for each network interface.

5. **List the PID/Program name:**
   ```bash
   sudo netstat -p
   ```
   Requires `sudo`. Shows the program name and PID associated with the connections.

6. **Continuous monitoring:**
   ```bash
   netstat -c
   ```
   Updates the output continuously in real-time (not supported on macOS).

---

### 2. **`lsof`** (List Open Files)

`lsof` stands for "list open files." It is a powerful tool for checking which files are open on the system and which processes are accessing them.

#### **Basic Usage**
```bash
lsof [options]
```

#### **Common Options for macOS:**
1. **List all open files:**
   ```bash
   lsof
   ```

2. **Show open files for a specific user:**
   ```bash
   lsof -u username
   ```

3. **Show open files by a specific process ID (PID):**
   ```bash
   lsof -p <PID>
   ```

4. **List network connections:**
   ```bash
   lsof -i
   ```
   Shows all open network connections.

5. **Show files opened by a specific port:**
   ```bash
   lsof -i :<port>
   ```
   For example, to see which process is using port `8080`:
   ```bash
   lsof -i :8080
   ```

6. **List files opened by a specific application:**
   ```bash
   lsof -c <appname>
   ```
   For example, if you want to see files opened by the browser:
   ```bash
   lsof -c Safari
   ```

7. **Show open files in a directory:**
   ```bash
   lsof +D /path/to/directory
   ```
   Lists all open files under a particular directory.

8. **Show only IPv4/IPv6 connections:**
   - For **IPv4**:
     ```bash
     lsof -i 4
     ```
   - For **IPv6**:
     ```bash
     lsof -i 6
     ```

9. **Show files opened by TCP/UDP:**
   ```bash
   lsof -i tcp
   lsof -i udp
   ```

10. **Combine flags:**
    You can also combine flags, e.g., show network files opened by a specific user:
    ```bash
    lsof -i -u username
    ```

---

### 3. **`fstat`** (File Stat, macOS alternative)

`fstat` is another tool available on macOS, often used in BSD-based systems. It lists open files by processes.

#### **Basic Usage**
```bash
fstat [options]
```

#### **Common Options for macOS:**
1. **List all open files:**
   ```bash
   fstat
   ```

2. **Show open files for a specific user:**
   ```bash
   fstat -u username
   ```

3. **Show open files by a specific process ID (PID):**
   ```bash
   fstat -p <PID>
   ```

4. **Show open files in a directory:**
   ```bash
   fstat -f /path/to/directory
   ```

---

### 4. **`ss`** (Socket Statistics, Linux alternative)

macOS lacks the `ss` command natively, but this is widely used on Linux. `ss` is a more modern replacement for `netstat` on Linux systems, offering faster and more detailed socket information. You could consider this if working on cross-platform systems.

---

### Summary of Key Commands:

| Command       | Description                                            |
|---------------|--------------------------------------------------------|
| `netstat -a`  | List all active network connections                    |
| `netstat -r`  | Display the routing table                              |
| `lsof`        | List all open files                                    |
| `lsof -i`     | Show open network files                                |
| `lsof -p PID` | Show open files by a specific process ID               |
| `fstat`       | List open files with a lightweight tool                |

---

### Learning Resources:

- **Man Pages**: `man netstat`, `man lsof`, and `man fstat` provide in-depth options and flags.
- **Online Tutorials**:
  - [DigitalOcean's Netstat Guide](https://www.digitalocean.com/community/tutorials/understanding-the-netstat-command)
  - [SS64 MacOS Command Guide](https://ss64.com/osx/)
