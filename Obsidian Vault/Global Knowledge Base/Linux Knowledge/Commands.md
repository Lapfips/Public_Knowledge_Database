
## File System Navigation

- `pwd`

Displays the current working directory.

**Example:**

```bash
/home/user
```
 
- `ls`

Lists the contents of a directory.

__Options__:  

`-l`: Displays a detailed list (permissions, owner, size, etc.).
`-a`: Shows hidden files (those that begin with a dot).
`-h`: Formats file sizes in a human-readable way (e.g., KB, MB, GB).
`-R`: Recursively lists the contents of directories.

**Example:**

```bash
drwxr-xr-x  2 user user 4.0K Oct  1 12:00 .
drwxr-xr-x  3 user user 4.0K Oct  1 11:59 ..
-rw-r--r--  1 user user  18K Oct  1 12:00 file.txt
```

- `cd`

Changes the current directory.

__Options__:

`cd -`: Returns to the previous directory.
`cd ~`: Navigates to the user’s home directory.

**Example:**
  
```bash
$ cd ~/Documents
```

---
## File and Directory Management

- `touch`  

Creates an empty file or updates the last modified timestamp if the file exists.

**Example:**

```bash
$ touch newfile.txt
```

- `mkdir`

Creates one or more directories.

__Options__:

`-p`: Creates parent directories as needed.

**Example:**

```bash
$ mkdir -p parent/child
```

- `rm`

Deletes files or directories.

__Options__:

`-r`: Recursively deletes directories and their contents.
`-f`: Forces deletion without asking for confirmation.

**Example:**

```bash
$ rm -rf directory
```

- `cp`

Copies files or directories.

__Options__:

`-r`: Recursively copies entire directories.
`-u`: Copies only if the source file is newer than the destination or if the destination does not exist.

**Example:**

```bash
$ cp -ru source destination
```

- `mv`  

Moves or renames files or directories.

**Example:**  

```bash
$ mv old_name new_name
```

- `ln`

Creates hard or symbolic (soft) links.

__Options__:

`-s`: Creates a symbolic link.

**Example:**

```bash
$ ln -s /path/to/original /path/to/link
```

---
## User and Permission Management

- `sudo`

Executes a command as the superuser (admin privileges).

**Example:**

```bash
$ sudo command
```

- `chmod`

Modifies the permissions of a file or directory.

__Syntax__:

- `u`: user (owner)
- `g`: group
- `o`: others
- `r`: read
- `w`: write
- `x`: execute

**Example to give execution rights to the owner:**  

```bash
$ chmod u+x script.sh
```

__Numeric permissions__:

- `4`: read
- `2`: write
- `1`: execute

**Example:**

```bash
$ chmod 755 file
```

- `chown`

Changes the ownership of a file or directory.

__Special case__:

Change both owner and group:  

**Example:**

```bash
$ chown user:group file.txt
```

---
## Process Management

- `ps`

Displays the currently running processes.

__Options__:

`aux`: Shows all running processes for all users.

**Example:**  

```bash
$ ps aux
```

- `top`

Displays active processes in real-time.

__Special case__:

To quit `top`:  

**Example:**

```bash
Press `q`
```

- `kill`

Terminates a process using its PID (Process ID).

__Special case__:

- `-9`: Forces termination of the process.

**Example:**

```bash
$ kill -9 1234
```

- `htop`

A more user-friendly version of `top` with interactive controls.

---
## Package Management

- `apt`

Package manager for Debian/Ubuntu-based distributions.

__Common commands__:

- **Example:**  

```bash
$ apt update
```

- **Example:**

```bash
$ apt upgrade
```

- **Example:**

```bash
$ apt install package
```

- **Example:**

```bash
$ apt remove package
```

- `dnf`

Package manager for Fedora-based distributions.

__Common commands__:

- **Example:**

```bash
$ dnf install package
```

- **Example:**

```bash
$ dnf update
```

- `yum`

Older package manager for RPM-based distributions like CentOS.

---
## Network and Connections

- `ping`

Tests network connectivity to an IP address or domain.

**Example:**

```bash
$ ping 8.8.8.8
```

- `ifconfig`

Displays or configures network interface parameters.

__Special case__:

To disable or enable a network interface:  

**Example:**

```bash
$ ifconfig eth0 down
```

**Example:**

```bash
$ ifconfig eth0 up
```

- `ip`  

Replaces `ifconfig` in many modern distributions for network management.

**Example to show IP addresses:**

```bash
$ ip addr show
```

- `netstat`

Displays network connections, routing tables, and port usage.  

__Options__:

`-tuln`: Lists open TCP and UDP ports.  

**Example:**

```bash
$ netstat -tuln
```

- `curl`

Transfers data to or from a server, useful for testing APIs or downloading files.

**Example:**

```bash
$ curl http://example.com
```

__Special case__:

To download a file:  

**Example:**

```bash
$ curl -O http://example.com/file.txt
```

- `wget`

Downloads files from the web.  

**Example:**

```bash
$ wget http://example.com/file.txt
```

- `ssh`

Remote connection from an host to another host or a serveur with his IP address

**Example**:

```shell
$ ssh <user_id>@<user_ip_address>
```

__Git and GitHub configuration with ssh__:

- Starts by creating an ssh key

```shell
$ ssh-keygen -t ed25519
```

- Copy the key on the remote desktop

```shell
$ ssh-copy-id <user_id>@<user_ip_address>
```

- Allow the ssh key in GitHub

```shell
$ cat ~/.ssh/id_ed25519.pub -> https://github.com/settings/keys
```

- Set the `.bash_profile` file to login with the passphrase and run all commands

```shell
echo "SSH_ENV="$HOME/.ssh/environment"

function start_agent {
     echo "Initialising new SSH agent..."
     /usr/bin/ssh-agent | sed 's/^echo/#echo/' > "${SSH_ENV}"
     echo succeeded
     chmod 600 "${SSH_ENV}"
     . "${SSH_ENV}" > /dev/null
     /usr/bin/ssh-add;
}

# Source SSH settings, if applicable

if [ -f "${SSH_ENV}" ]; then
     . "${SSH_ENV}" > /dev/null
     #ps ${SSH_AGENT_PID} doesn't work under cywgin
     ps -ef | grep ${SSH_AGENT_PID} | grep ssh-agent$ > /dev/null || {
         start_agent;
     }
else
     start_agent;
fi" > .bash_profile

. .bash_profile
```

- `Git / GitHub`

Works on saved files on `GitHub`

__Configure__:

```shell
git config --global user.email "<personal_email>
git config --global user.name "<username>"
```

**Example**

```shell
git clone git@github.com:<repository_name>/<folder_name>.git
```

__Update__:

```shell
git add .
git commit -m "<message>"
git push
```

---
## Other Useful Commands

- `df`

Displays disk space usage.

__Options__:

`-h`: Shows sizes in a human-readable format (e.g., KB, MB, GB).

**Example:**

```bash
$ df -h
```

- `du`

Shows disk usage for files and directories.

__Options__:

`-sh`: Summarizes the size of a directory in a human-readable format.

**Example:**

```bash
$ du -sh directory
```

- `tar`

Creates or extracts compressed archives.

__Common cases__:

- Create a compressed archive:  

  **Example:**

```bash
$ tar -czvf archive.tar.gz directory
```

- Extract a compressed archive:  

  **Example:**

```bash
$ tar -xzvf archive.tar.gz
```

- `grep`

Searches for a string in files.

__Options__:

`-r`: Recursively searches within subdirectories.
`-i`: Ignores case.

**Example:**

```bash
$ grep -ri "pattern" directory
```

- `find`

Searches for files and directories.

__Options__:

`-name`: Search by file name.
`-type f`: Search for files.
`-type d`: Search for directories.

**Example:**

```bash
$ find /path -name "*.txt"
```

- `locate`

Quickly finds files by name (requires pre-indexing with `updatedb`).

**Example:**

```bash
$ locate file.txt
```