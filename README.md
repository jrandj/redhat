# Redhat

## RHCSA

### Understand and use essential tools

1. Command commands and their options are shown below:

| Command        | Options                                                                                                                                                          | Description                                     |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| ls             | -h (human readable) <br>  -a (show hidden) <br> -l (detailed) <br> -lt (newist file first) <br> -ltr (oldest file first)                                         | List of files and directories                   |
| pwd            |                                                                                                                                                                  | Print working directory                         |
| cd             | ~ (home) <br> / (root) <br> - (switch) <br> .. (parent)                                                                                                          | Change directories                              |
| who            | whoami (show user)                                                                                                                                               | Show logged in users                            |
| what           | w (shorthand)                                                                                                                                                    | Show logged in users with more detail           |
| uptime         |                                                                                                                                                                  | Show system uptime                              |
| logname        |                                                                                                                                                                  | Show real username (if using su)                |
| id             |                                                                                                                                                                  | Shows a user's UID, username, GUID etc.         |
| groups         |                                                                                                                                                                  | Lists groups for users                          |
| last           |                                                                                                                                                                  | List all user logins and system reboots         |
| lastb          |                                                                                                                                                                  | List all failed login attempts                  |
| lastlog        |                                                                                                                                                                  | List recent logins                              |
| uname          | -a (details)                                                                                                                                                     | System information                              |
| hostnamectl    | set-hostname                                                                                                                                                     | View hostname                                   |
| clear          |                                                                                                                                                                  | Clear the screen                                |
| timedatectl    | set-time <br> list-timezones <br> set-timezone <br>                                                                                                              | Display system time                             |
| date           | --set                                                                                                                                                            | View system date                                |
| which          |                                                                                                                                                                  | Show path to a command                          |
| wc             |                                                                                                                                                                  | Word count                                      |
| lspci          | -m (legible)                                                                                                                                                     | PCI buses details                               |
| lsusb          |                                                                                                                                                                  | USB buses details                               |
| lscpu          |                                                                                                                                                                  | Processor details                               |
| gzip/bzip2     | -d (uncompress)                                                                                                                                                  | Compress files                                  |
| gunzip/bunzip2 |                                                                                                                                                                  | Uncompress files                                |
| tar            | -c (create) <br> -f (specifies name) <br> -v (verbose) <br> -r (append to existing) <br> -x (extract) <br> -z (compress with gzip) <br> -j (compress with bzip2) | Archive file                                    |
| star           |                                                                                                                                                                  | Enhanced tar                                    |
| man            | -k (keyword) <br> -f (short description)                                                                                                                         | Manual                                          |
| mandb          |                                                                                                                                                                  | Update the mandb                                |
| ssh            | -l (as different user)                                                                                                                                           | SSH to another Linux system                     |
| tty            |                                                                                                                                                                  | Display terminal name                           |
| whatis         |                                                                                                                                                                  | Search the command in the mandb for description |
| info           |                                                                                                                                                                  | More detailed than man                          |
| apropos        |                                                                                                                                                                  | Search the command in the mandb                 |

1. Vim usage is shown below:

### Operate running systems

### Configure local storage

### Create and configure file systems

### Deploy, configure, and maintain systems

### Manage basic networking

### Manage users and groups

### Manage security