# Redhat

## RHCSA

- [Understand and use essential tools](#Understand-and-use-essential-tools)
- [Operate running systems](#Operate-running-systems)
- [Configure local storage](#Configure-local-storage)
- [Create and configure file systems](#Create-and-configure-file-systems)
- [Deploy, configure, and maintain systems](#Deploy,-configure,-and-maintain-systems)
- [Manage basic networking](#Manage-basic-networking)
- [Manage users and groups](#Manage-users-and-groups)
- [Manage security](#Manage-security)

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
    * The version of SSH used is defined in */etc/ssh/sshd_config*.
    * The most common authentication methods are Password-Based Authentication and Public/Private Key-Based Authentication.
    * The command *ssh-keygen* is used to generate keys and place them in the .ssh directory, and the command *ssh-copy-id* is used to copy the public key file to your account on the remote server.
    * TCP Wrappers is a host-based mechanism that is used to limit access to wrappers-aware TCP services on the system by inbound clients. Two files */etc/hosts.allow* and */etc/hosts.deny* are used to control access. The .allow file is referenced before the .deny file. The format of the files is \<name of service process>:\<user@source>.
    * All messages related to TCP Wrappers are logged to the */var/log/secure* file.


1. Log in and switch users in multiuser targets

    * A user can switch to another user using the *su* command. The -i option ensures that the target users login scripts are run:

        ```shell
        sudo -i -u targetUser
        ``` 
    * To run a command as root without switching:
    
        ```shell
        sudo -c
        ``` 
    * The configuration for which users can run which commands using sudo is defined in the */etc/sudoers* file. The visudo command is used to edit the sudoers file. The sudo command logs successful authentication and command data to */var/log/secure*.

1. Archive, compress, unpack, and uncompress files using tar, star, gzip, and bzip2

    * To archive using tar:

        ```shell
        tar cvf myTar.tar /home
        ``` 

    * To unpack using tar:

        ```shell
        tar xvf myTar.tar
        ``` 

    * To compress using tar and gzip:

        ```shell
        tar cvfz myTar.tar /home
        ``` 

    * To compress using tar and bzip2:

        ```shell
        tar cvfj myTar.tar /home
        ``` 

    * To uncompress using tar and gzip:

        ```shell
        tar xvfz myTar.tar /home
        ``` 

    * To uncompress using tar and bzip2:

        ```shell
        tar xvfj myTar.tar /home
        ``` 

    * The star command is an enhanced versin of tar. It also supports SELinux security contexts and extended file attributes. The options are similar to tar.


1. Create and edit text files

    * To create an empty file:

        ```shell
        touch file
        cat > newfile
        ``` 

    * To create a vile using vim:
    
        ```shell
        vi file
        ``` 

1. Create, delete, copy, and move files and directories

    * To create a directory:

        ```shell
        mkdir directory
        ``` 

    * To move a file or directory:

        ```shell
        mv item1 item2
        ```     

    * To copy a file or directory:

        ```shell
        cp item1 item2
        ```     

    * To remove a file:

        ```shell
        rm file1
        ```

    * To remove an empty directory:

        ```shell
        rmdir directory
        ```

    * To remove a non-empty directory:

        ```shell
        rm -r directory
        ```

1. Create hard and soft links

    * A soft link associates one file with another. If the original file is removed the soft link will point to nothing. To create a softlink to file1:

        ```shell
        ln -s file1 softlink
        ``` 

    * A hard link associates multiple files to the same inode making them indistinguishable. If the original file is removed, you will still have access to the data through the linked file. To create a softlink to file1:

        ```shell
        ln file1 hardlink
        ``` 

1. List, set, and change standard ugo/rwx permissions

    * Permissions are set for the user, group and others. User is the owner of the file or the directory, group is a set of users with identical access defined in */etc/group*, and others are all other users. The types of permission are read, write and execute.
    * Permission combinations are shown below:

        | Octal Value | Binary Notation | Symbolic Notation | Explanation                           |
        |-------------|-----------------|-------------------|---------------------------------------|
        | 0           | 000             | ---               | No permissions.                       |
        | 1           | 001             | --x               | Execute permission only.              |
        | 2           | 010             | -w-               | Write permission only.                |
        | 3           | 011             | -wx               | Write and execute permissions.        |
        | 4           | 100             | r--               | Read permission only.                 |
        | 5           | 101             | r-x               | Read and execute permissions.         |
        | 6           | 110             | rw-               | Read and write permissions.           |
        | 7           | 111             | rwx               | Read, write, and execute permissions. |

    * To grant the owner, group and others all permissions using the *chmod* command:

        ```shell
        chmod 777 file1
        ```
    * The default permissions are calculated based on the umask. The default umask for root is 0022 and 0002 for regular users (the leading 0 has no significance). The pre-defined initial permissions are 666 for files and 777 for directories. The umask is subtracted from these initial permissions to obtain the default permissions. To change the default umask:

        ```shell
        umask 027
        ```
    * Every file and directory has an owner. By default, the creator assumes ownership. The owner's group is assigned to a file or directory. To change the ownership of a file or directory:

        ```shell
        useradd user100
        chown user100 item1
        chgrp user100 item1
        ```
    
        ```shell
        chown user100:user100 item1
        ```
    * Note that the -R option must be used to recusively change all files in a directory.

1. Locate, read, and use system documentation including man, info, and files in */usr/share/doc*

    * The *man* command can be used to view help for a command. To search for a command based on a keyword the *apropros* command or *man* with the -k option can be used. The *mandb* command is used to build the man database.

    * The *whatis* command can be used to search for a command in the man database for a short descripton.

    * The *info* command provides more detailed information than the *man* command. 

    * The */usr/share/doc* directory contains documentation for all installed packages under sub-directories that match package names followed by their version.

### Operate running systems

1. Boot, reboot, and shut down a system normally

    * The RHEL boot process occurs when the system is powered up or reset, and lasts until all enabled services are started and a login prompt appears at the screen. The login process consists of 4 steps:

        * The firmware is the Basic Input Output System (BIOS) or Unified Extensible Firmware Interface (UEFI) code that is stored in flash memory on the motherboard. The first thing it does is run the power-on-self-test (POST) to initialise the system hardware components. It also installs appropriate drivers for the video hardware and displays system messages to the screen. It scans the available storage devices to locate a boot device (GRUB2 on RHEL), and then loads it into memory and passes control to it.

        * The boot loader presents a menu with a list of bootable kernels available on the system. After a pre-defined amount of time it boots the default kernel. GRUB2 searches for the kernel in the */boot* file system. It then extracts the kernel code into memory and loads it based on the configuration in */boot/grub2/grub.cfg*. Note that for UEFI systems, GRUB2 looks in */boot/efi* instead and loads based on configuration in */boot/efi/EFI/redhat/grub.efi*. Once the kernel is loaded, GRUB2 passes control to it.

        * The kernel loads the initial RAM disk (initrd) image from the */boot* file system. This acts as a temporary file system. The kernal then loads necessary modules from initrd to allow access to the physical disks and the partitions and file systems within. It also loads any drivers required to support the boot process. Later, the kernal unmounts initrd and mounts the actual root file system.

        * The kernel continues the boot process. *systemd* is the default system initilisation scheme. It starts all enabled userspace system and network services.

    * The *shutdown* command is used to halt, power off, or reboot the system gracefully. This command broadcasts a warning message to all logged-in users, disables further user logins, waits for the specified time, and then stops the service and shuts to the system down to the specified target state. 
    
    * To shut down the system now:
        ```shell
        shutdown -P now
        ```

    * To halt the system now:
        ```shell
        shutdown -H now
        ```

    * To reboot the system now:
        ```shell
        shutdown -r now
        ```

    * To shut down the system after 5 minutes:
        ```shell
        shutdown -P 5
        ```

1. Boot systems into different targets manually

    * *systemd* is the default system initialisation mechanism in RHEL8. It is the first process that starts at boot and it is the last process that terminates at shutdown.

    * *Units* are systemd objects that are used for organising boot and maintenance tasks, such as hardware initialisation, socket creation, file system mounts, and service startups. Unit configuration is stored in their respective configuration files, which are auto-generated from other configurations, created dynamically from the system state, produced at runtime, or userdeveloped. Units are in one of several operational states, including active, inactive, in the process of being activated or deactivated, and failed. Units can be enabled or disabled.

    * Units have a name and a type, which are encoded in files of the form unitname.type. Units can be viewed using the *systemctl* command. A target is a logical collection of units. They are a special systemd unit type with the .target file extension.

    * *systemctl* is the primary command for interaction with systemd. 

    * To boot into a custom target the *e* key can be pressed at the GRUB2 menu, and the desired target specified using systemd.unit. After editing press *Ctrl+x* to boot into the target state. To boot into the emergency target: 
        ```shell
        systemd.unit=emergency.target
        ```

    * To boot into the rescue target:
        ```shell
        systemd.unit=rescue.target
        ```

    * Run *systemctl reboot* after you are done to reboot the system.

1. Interrupt the boot process in order to gain access to a system

    * Press *e* at the GRUB2 menu and add "rd.break" in place of "ro crash". 
    * Press *Ctrl+x* to reboot.
    * Run the following command to remount root with rw:
        ```shell
        mount -o remount,rw /sysroot
        ```
    *  Run the following command to change the root directory:
        ```shell
        chroot /sysroot
        ```
    *  Run *passwd* command to change the password.
    *  Run the following commands to create an empty, hidden file to instruct the system to perform SELinux relabeling after the next boot:
        ```shell
        touch /.autorelabel
        exit
        exit
        ```

1. Identify CPU/memory intensive processes and kill processes

    * A process is a unit for provisioning system resources. A process is created in memory in its own address space when a program, application, or command is initiated. Processes are organised in a heirarchical fashion. Each process has a parent process that spawns it, and may have one or many child processes. Each process is assigned a unique identification number, known as the Process Identifier (PID). When a process completes its lifecycle or is terminated, this event is reported back to its parent process, and all the resources provisioned to it are then freed and the PID is removed. Processes spawned at system boot are called daemons. Many of these sit in memory and wait for an event to trigger a request to use their services.

    * There are 5 basic process states:
        * Running: The process is being executed by the CPU.
        * Sleeping: The process is waiting for input from a user or another process.
        * Waiting: The process has received the input it was waiting for and is now ready to run when its turn arrives.
        * Stopped: The process is halted and will not run even when its turn arrives, unless a signal is sent to change its behaviour.
        * Zombie: The process is dead. Its entry is retained until the parent process permits it to die.

    * The *ps* and *top* commands can be used to view running processes.
    
    * The *pidof* or *pgrep* commands can be used to view the PID associated with a process name.
    
    * The *ps* command can be used to view the processes associated with a particular user. An example is shown below:
        ```shell
        ps -U root
        ```

    * To kill a process the *kill* or *pkill* commands can be used. Ordinary users can kill processes they own, while the *root* user can kill any process. The *kill* command requires a PID and the *pkill* command requires a process name. An example is shown below:
        ```shell
        pkill crond
        kill `pidof crond`
        ```
    * The list of signals accessible by *kill* can be seen by passing the *-l* option. The default signal is SIGTERM which signals for a process to terminate in an orderly fashion.

    * To use the SIGKILL signal:
        ```shell
        pkill -9 crond
        kill -9 `pgrep crond`
        ```

    * The *killall* command can be used to terminate all processes that match a specified criteria.
    
1. Adjust process scheduling

    * The priority of a process ranges from -20 (highest) to +19 (lowest). A higher niceness lowers the execution priority of a process and a lower niceness increases it. A child process inherits the niceness of its parent process.

    * To run a command with a lower (+2) priority:
        ```shell
        nice -2 top
        ```

    * To run a command with a higher (-2) priority:
        ```shell
        nice --2 top
        ```

    * To renice a running process:
        ```shell
        renice 5 1919
        ```
    
1. Manage tuning profiles

    * Tuned is a service which monitors the system and optimises the performance of the system for different use cases. There are pre-defined tuned profiels available in the */usr/lib/tuned* directory. New profiles are created in the */etc/tuned* directory. The *tuned-adm* command allows you to interact with the Tuned service.

    * To install and start the tuned service:
        ```shell
        yum install tuned
        systemctl enable --now tuned
        ```
 
    * To check the currently active profile:
        ```shell
        tuned-adm active
        ```

    * To check the recommended profile:
        ```shell
        tuned-adm recommend
        ```

    * To change the active profile:
        ```shell
        tuned-adm profile <profile-name>
        ```

    * To create a customised profile and set it as active:
        ```shell   
        mkdir /etc/tuned/<profile-name>
        vi /etc/tuned/<profile-name>/<profile-name.conf>
        # customise as required
        tuned-adm profile <profile-name>
        systmctl restart tuned.service
        ```

1. Locate and interpret system log files and journals

1. Preserve system journals

1. Start, stop, and check the status of network services

1. Securely transfer files between systems

### Configure local storage

1. List, create, delete partitions on MBR and GPT disks

1. Create and remove physical volumes

1. Assign physical volumes to volume groups

1. Create and delete logical volumes

1. Configure systems to mount file systems at boot by universally unique ID (UUID) or label

1. Add new partitions and logical volumes, and swap to a system non-destructively

### Create and configure file systems

1. Create, mount, unmount, and use vfat, ext4, and xfs file systems

1. Mount and unmount network file systems using NFS

1. Extend existing logical volumes

1. Create and configure set-GID directories for collaboration

1. Configure disk compression

1. Manage layered storage

1. Diagnose and correct file permission problems

### Deploy, configure, and maintain systems

1. Schedule tasks using at and cron

    * Job scheduling and execution is handled by the *atd* and *crond* daemons. While *atd* manages jobs scheduled to run once in the future, *crond* is responsbile for running jobs repetitively at pre-specified times. At startup, *crond* reads schedules in files located in the */var/spool/cron* and */etc/cron.d* directories, and loads them in memory for later execution.

    * There are 4 files that control permissions for setting scheduled jobs. These are *at.allow*, *at.deny*, *cron.allow* and *cron.deny*. These files are located in the */etc* directory. The syntax of the files is identical, with each file taking 1 username per line. If no files exist, then no users are permitted. By default, the *deny* files exist and are empty, and the *allow* files do not exist. This opens up full access to using both tools for all users.

    * All activities involving *atd* and *crond* are logged to the */var/log/cron* file.

    * The *at* command is used to schedule one-time execution of a program by the *atd* daemon. All submitted jobs are stored in the */var/spool/at* directory.

    * To schedule a job using *at* the below syntax is used:
        ```shell
        at 11:30pm 6/30/15
        ```
    * The commands to execute are defined in the terminal, press *Ctrl+d* when finished. The added job can be viewed with *at* and can be removed with the *-d* option.

    * A shell script can also be provided:
        ```shell
        at -f ~/script1.sh 11:30pm 6/30/15
        ```

    * The */etc/crontab* file has the following columns:
        * 1: Minutes of hour (0-59), with multiple comma seperated values, or * to represent every minute.
        * 2: Hours of day (0-23), with multiple comma seperated values, or * to represent every hour.
        * 3: Days of month (1-31), with multiple comma seperated values, or * to represent every day.
        * 4: Month of year (1-12, jan-dec), with multiple comma seperated values, or * to represent every month.
        * 5: Day of week (0-6, sun-sat), with multiple comma seperated values, or * to represent every day.
        * 6: Full path name of the command or script to be executed, along with any arguments.
        
    * Step values can be used with */2 meaning every 2nd minute.
    
    * The *crontab* command can be used to edit the file. Common options are *e* (edit), *l* (view), *r* (remove):
        ```shell
        crontab -e
        ```

1. Start and stop services and configure services to start automatically at boot

1. Configure systems to boot into a specific target automatically

1. Configure time service clients

1. Install and update software packages from Red Hat Network, a remote repository, or from the local file system

1. Work with package module streams

1. Modify the system bootloader

### Manage basic networking

### Manage users and groups

### Manage security