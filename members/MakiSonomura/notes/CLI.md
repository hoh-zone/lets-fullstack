# CLI


## Linux/Unix



### 1. **File Management**

- **`cp` (Copy)**: Copies files or directories.
    ```bash
    cp source_file destination_file
    cp -r source_directory destination_directory  # For directories
    ```

- **`mv` (Move/Rename)**: Moves files or directories. Also used for renaming.
    ```bash
    mv old_file new_file
    mv file /path/to/new_location/
    ```

- **`rm` (Remove)**: Deletes files or directories.
    ```bash
    rm file_name
    rm -r directory_name  # Use with caution, as it deletes recursively!
    ```

- **`mkdir` (Make Directory)**: Creates a new directory.
    ```bash
    mkdir new_directory
    ```

---

### 2. **System Monitoring**

- **`top`**: Shows a live view of processes, including CPU and memory usage.
    ```bash
    top
    ```

- **`ps` (Process Status)**: Lists active processes. Used with options to see detailed info.
    ```bash
    ps aux    # Lists all processes with detailed information
    ```

- **`df` (Disk Free)**: Shows the amount of disk space available on the filesystem.
    ```bash
    df -h    # "-h" for human-readable output, like GB or MB
    ```

- **`free`**: Displays memory usage, showing free and used memory.
    ```bash
    free -h   # "-h" for human-readable format
    ```

---

### 3. **Networking**

- **`ping`**: Sends packets to check connectivity with a network or internet host.
    ```bash
    ping example.com
    ```

- **`netstat` (Network Statistics)**: Displays network connections, routing tables, and network interfaces.
    ```bash
    netstat -a   # Shows all active connections
    ```

- **`curl`**: Transfers data from or to a server. Often used to test APIs or download files.
    ```bash
    curl https://example.com
    ```

- **`iptables`**: Configures the Linux kernel firewall.
    ```bash
    sudo iptables -L    # Lists current firewall rules
    ```

---

### 4. **Software Installation and Updates**

- **`apt`** (Debian-based systems): Manages packages on distributions like Ubuntu or Debian.
    ```bash
    sudo apt update           # Updates the package list
    sudo apt install package  # Installs a package
    ```

- **`yum`** (Red Hat-based systems): Package manager for Red Hat, CentOS, etc.
    ```bash
    sudo yum install package  # Installs a package
    ```

- **`dnf`** (Newer Red Hat-based systems): Replaces `yum` in Fedora and newer Red Hat versions.
    ```bash
    sudo dnf install package  # Installs a package
    ```

---

### 5. **Automation and Scripting**

Shell scripting uses commands and logic within a script (usually Bash) to automate tasks. Here’s a simple example:

```bash
#!/bin/bash
# Script to check if a directory exists

DIR="/path/to/directory"
if [ -d "$DIR" ]; then
    echo "Directory exists."
else
    echo "Directory does not exist."
fi
```
Certainly! Here’s a further list of commonly used Linux commands, with explanations and examples:

---

### 6. **File Viewing and Searching**

- **`cat` (Concatenate)**: Displays the contents of a file.
    ```bash
    cat file_name
    ```

- **`less`**: Opens a file in a scrollable view, useful for reading long files.
    ```bash
    less file_name
    ```

- **`grep`**: Searches for a pattern in a file or output.
    ```bash
    grep "search_term" file_name
    ```

- **`find`**: Finds files or directories by name, type, or other attributes.
    ```bash
    find /path -name "file_name"
    ```

- **`locate`**: Searches for files in the system (uses a database, so it’s faster than `find`).
    ```bash
    locate file_name
    ```

---

### 7. **File Compression and Archiving**

- **`tar`**: Archives multiple files into a single file (often `.tar`, `.tar.gz`, or `.tgz`).
    ```bash
    tar -czvf archive_name.tar.gz /path/to/directory   # Creates a compressed archive
    tar -xzvf archive_name.tar.gz                       # Extracts an archive
    ```

- **`gzip`**: Compresses a single file.
    ```bash
    gzip file_name     # Compresses to file_name.gz
    gunzip file_name.gz  # Decompresses
    ```

- **`zip` and `unzip`**: Compresses and decompresses files into `.zip` format.
    ```bash
    zip archive_name.zip file1 file2
    unzip archive_name.zip
    ```

---

### 8. **User Management**

- **`adduser`**: Creates a new user.
    ```bash
    sudo adduser new_username
    ```

- **`deluser`**: Deletes a user.
    ```bash
    sudo deluser username
    ```

- **`passwd`**: Changes the password for a user.
    ```bash
    sudo passwd username
    ```

- **`usermod`**: Modifies a user account, like adding to groups.
    ```bash
    sudo usermod -aG groupname username
    ```

---

### 9. **Permissions and Ownership**

- **`chmod`**: Changes the permissions of a file or directory.
    ```bash
    chmod 755 file_name    # rwxr-xr-x permissions
    ```

- **`chown`**: Changes the ownership of a file or directory.
    ```bash
    sudo chown username:groupname file_name
    ```

---

### 10. **Text Manipulation**

- **`echo`**: Outputs text to the terminal or a file.
    ```bash
    echo "Hello, world!"
    echo "Text" > file_name    # Writes text to file
    ```

- **`awk`**: A powerful text processing tool used for pattern scanning and processing.
    ```bash
    awk '{print $1}' file_name   # Prints the first column of each line
    ```

- **`sed`**: Stream editor for editing files or streams of text, often used for substitutions.
    ```bash
    sed 's/old_text/new_text/g' file_name  # Replaces 'old_text' with 'new_text'
    ```

---

### 11. **Networking and Connections**

- **`wget`**: Downloads files from the internet.
    ```bash
    wget https://example.com/file.zip
    ```

- **`scp` (Secure Copy)**: Copies files over SSH to/from remote servers.
    ```bash
    scp file_name username@remote_host:/path/to/destination
    ```

- **`ssh` (Secure Shell)**: Connects to remote servers over SSH.
    ```bash
    ssh username@remote_host
    ```

---

### 12. **System Information**

- **`uname`**: Displays system information.
    ```bash
    uname -a   # Shows all system information
    ```

- **`hostname`**: Displays or sets the hostname.
    ```bash
    hostname    # Displays the current hostname
    ```

- **`uptime`**: Shows how long the system has been running.
    ```bash
    uptime
    ```

---

### 13. **Disk and File System Utilities**

- **`mount`**: Mounts a filesystem to a specified directory.
    ```bash
    sudo mount /dev/sdX /mnt/point
    ```

- **`umount`**: Unmounts a filesystem from a directory.
    ```bash
    sudo umount /mnt/point
    ```

- **`fsck` (File System Check)**: Checks and repairs a filesystem.
    ```bash
    sudo fsck /dev/sdX
    ```

---

### 14. **Date and Time Management**

- **`date`**: Displays or sets the system date and time.
    ```bash
    date   # Shows current date and time
    ```

- **`cal`**: Displays a calendar for a specified month or year.
    ```bash
    cal 2024   # Shows the calendar for the year 2024
    ```

---

### 15. **Process Management**

- **`kill`**: Terminates a process by ID.
    ```bash
    kill process_id
    ```

- **`pkill`**: Kills processes by name.
    ```bash
    pkill process_name
    ```

- **`killall`**: Kills all instances of a process.
    ```bash
    killall process_name
    ```

--- 


## Windows

### Prerequisite

`Windows Terminal` is a new terminal emulator that lets you run PowerShell, Command Prompt, Azure, or WSL. I recommend installing it! If you'd like installation instructions, check out the next note.



### 1. **File Management**

- **`dir`**: Lists files and directories in the current directory.
    ```cmd
    dir
    ```

- **`copy`**: Copies files from one location to another.
    ```cmd
    copy source_file destination_file
    ```

- **`move`**: Moves files from one location to another. Can also be used for renaming.
    ```cmd
    move old_file new_file
    ```

- **`del`**: Deletes files.
    ```cmd
    del file_name
    ```

- **`mkdir`**: Creates a new directory.
    ```cmd
    mkdir new_directory
    ```

- **`rmdir`**: Removes an empty directory. Use `/s` to remove directories and their contents.
    ```cmd
    rmdir directory_name /s
    ```

---

### 2. **System Information**

- **`systeminfo`**: Displays detailed information about the system, like OS version, memory, etc.
    ```cmd
    systeminfo
    ```

- **`hostname`**: Shows the computer’s hostname.
    ```cmd
    hostname
    ```

- **`tasklist`**: Lists all running processes.
    ```cmd
    tasklist
    ```

- **`taskkill`**: Ends a running process by name or process ID.
    ```cmd
    taskkill /IM process_name.exe /F
    ```

---

### 3. **Networking**

- **`ipconfig`**: Shows network information, like IP address, subnet mask, and default gateway.
    ```cmd
    ipconfig
    ```

- **`ping`**: Checks connectivity to another network device or internet host.
    ```cmd
    ping example.com
    ```

- **`netstat`**: Displays active connections, routing tables, and network interface statistics.
    ```cmd
    netstat -a
    ```

- **`tracert`**: Shows the route taken by packets to reach a destination.
    ```cmd
    tracert example.com
    ```

- **`nslookup`**: Looks up DNS information for a domain.
    ```cmd
    nslookup example.com
    ```

---

### 4. **User Management**

- **`net user`**: Views or manages user accounts.
    ```cmd
    net user  # Lists all users
    net user username password /add  # Adds a user with specified password
    ```

- **`net localgroup`**: Views or manages local groups.
    ```cmd
    net localgroup administrators  # Lists members of the Administrators group
    ```

---

### 5. **File Permissions and Ownership**

- **`icacls`**: Modifies file and folder permissions.
    ```cmd
    icacls "file_name" /grant username:F   # Grants full access
    ```

- **`attrib`**: Views or changes file attributes (like read-only, hidden).
    ```cmd
    attrib +r file_name  # Makes a file read-only
    ```

---

### 6. **File Compression and Archiving**

- **`compact`**: Compresses files or displays the compression status of files.
    ```cmd
    compact /c file_name  # Compresses the file
    ```

- **`tar` (in Windows 10+ PowerShell)**: Creates or extracts tar archives.
    ```powershell
    tar -cvf archive_name.tar directory_path  # Creates an archive
    tar -xvf archive_name.tar  # Extracts an archive
    ```

---

### 7. **Text Manipulation**

- **`echo`**: Displays messages or outputs text to a file.
    ```cmd
    echo Hello, world!
    echo Text > file_name.txt  # Writes "Text" to a file
    ```

- **`findstr`**: Searches for text within files (similar to `grep` in Linux).
    ```cmd
    findstr "search_term" file_name.txt
    ```

---

### 8. **System Configuration and Maintenance**

- **`chkdsk`**: Checks for disk errors and repairs them.
    ```cmd
    chkdsk C: /f
    ```

- **`sfc`**: Scans and repairs system files.
    ```cmd
    sfc /scannow
    ```

- **`diskpart`**: Opens a disk partitioning tool (use with caution).
    ```cmd
    diskpart
    ```

---

### 9. **PowerShell Specific Commands**

- **`Get-Process`**: Lists all running processes (similar to `tasklist` in CMD).
    ```powershell
    Get-Process
    ```

- **`Get-Service`**: Lists all services and their statuses.
    ```powershell
    Get-Service
    ```

- **`Start-Process`**: Starts a process.
    ```powershell
    Start-Process "notepad.exe"
    ```

- **`Stop-Process`**: Ends a process.
    ```powershell
    Stop-Process -Name "process_name" -Force
    ```

---

### 10. **System Date and Time**

- **`date`**: Displays or sets the system date.
    ```cmd
    date   # Displays current date and prompts to change it
    ```

- **`time`**: Displays or sets the system time.
    ```cmd
    time   # Displays current time and prompts to change it
    ```

---
