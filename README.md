# Redhat

## RHCSA

### Understand and use essential tools
1. Access a shell prompt and issue commands with correct syntax
    * Common commands and their options, as well as vim usage, are shown below:
    
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
        | grep           | -n (show line numbers) <br> -v (pattern exclusion) <br> -i (case insensitive) <br> -E (use alternation) <br> -w (word match)                                     | Find text                                       |
        
        | Key                      | Description                     |
        |--------------------------|---------------------------------|
        | i                        | Change to insert mode           |
        | h, j, k, l               | Move left, down, up, right      |
        | w, b, e, ge              | Move word at a time             |
        | n[action]                | Do n times                      |
        | x                        | Remove a character              |
        | a                        | Append                          |
        | f[char]                  | Move to next given char in line |
        | F[char]                  | Move to previous char in line   |
        | ; and ,                  | Repeat last f or F              |
        | /yourtext and then: n, N | Search text                     |
        | d[movement]              | Delete by giving movement       |
        | r[char]                  | Replaces character below cursor |
        | 0, $                     | Move to start/end of line       |
        | o, O                     | Add new line                    |
        | %                        | Goto corresponding parentheses  |
        | ci[movement]             | Change inside of given movement |
        | D                        | Delete to end of line           |
        | S                        | Clear current line              |
        | gg / G                   | Move to start / end of buffer   |
        | yy                       | Copy current line               |
        | p                        | Paste copied text after cursor  |
    
1. Use input-output redirection (>, >>, |, 2>, etc.)
    * The default locations for input, output, and error are referred to as standard input (stdin), standard output (stdout), and standard error (stderr).
    * Standard input redirection can be done to have a command read the required information from an alternative source, such as a file, instead of the keyboard. For example:
    
        ```shell
        cat < /etc/cron.allow 
        ```
    * Standard output redirection sends the output generated by a command to an alternative destination, such as a file. For example:
    
        ```shell
        ll > ll.out
        ```
    * Standard error redirection sends the output generated by a command to an alternative destination, such as a file. For example: 
       
        ```shell
        echo test 2> outerr.out
        ```
    * Instead of > to create or overwrite, >> can be used to append to a file.
1. Use grep and regular expressions to analyze text
    * The grep command is used to find text. For example:
    
        ```shell
        grep user100 /etc/passwd
        ```    
    * Common regular expression parameters are shown below:
    
        | Symbol | Description                                                        |
        |--------|--------------------------------------------------------------------|
        | ^      | Beginning of a line or word                                        |
        | $      | End of a line or word                                              |
        | \|     | Or                                                                 |
        | .      | Any character                                                      |
        | *      | Any number of any character                                        |
        | ?      | Exactly one character                                              |
        | []     | Range of characters                                                |
        | \      | Escape character                                                   |
        | ''     | Mask meaning of enclosed special characters                        |
        | ""     | Mask meaning of all enclosed special characters except \, $ and '' |
    
1. Access remote systems using SSH

    * Secure Shell (SSH) provides a secure mechanism for data transmission between source and destination systems over IP networks.
    * SSH uses encryption and performs data integrity checks on transmitted data.
    * The version of SSH used is defined in /etc/ssh/sshd_config.
    * The most common authentication methods are Password-Based Authentication and Public/Private Key-Based Authentication.
    * The command ssh-keygen is used to generate keys and place them in the .ssh directory, and the command ssh-copy-id is used to copy the public key file to your account on the remote server.
    * TCP Wrappers is a host-based mechanism that is used to limit access to wrappers-aware TCP services on the system by inbound clients. Two files /etc/hosts.allow and /etc/hosts.deny are used to control access. The .allow file is referenced before the .deny file. The format of the files is \<name of service process>:\<user@source>.
    * All messages related to TCP Wrappers are logged to the /var/log/secure file.


1. Log in and switch users in multiuser targets
1. Archive, compress, unpack, and uncompress files using tar, star, gzip, and bzip2
1. Create and edit text files
1. Create, delete, copy, and move files and directories
1. Create hard and soft links
1. List, set, and change standard ugo/rwx permissions
1. Locate, read, and use system documentation including man, info, and files in /usr/share/doc

### Operate running systems

### Configure local storage

### Create and configure file systems

### Deploy, configure, and maintain systems

### Manage basic networking

### Manage users and groups

### Manage security