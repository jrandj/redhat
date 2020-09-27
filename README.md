# Redhat

## RHCSA

- [Understand and use essential tools](#Understand-and-use-essential-tools)
- [Operate running systems](#Operate-running-systems)
- [Configure local storage](#Configure-local-storage)
- [Create and configure file systems](#Create-and-configure-file-systems)
- [Deploy, configure, and maintain systems](#Deploy-configure-and-maintain-systems)
- [Manage basic networking](#Manage-basic-networking)
- [Manage users and groups](#Manage-users-and-groups)
- [Manage security](#Manage-security)
- [Exercises](#Exercises)

### Understand and use essential tools
1. Programmable completion for bash is provided in the bash-completion module. To install this module:
    ```shell
    sudo dnf install bash-completion
    ```

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
    
    * To login using SSH: 
        ```shell
        ssh user@host
        ``` 

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

    * To search for a command based on a keyword in occuring in its man page:
        ```shell
        man -K <keyword>
        ```

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

    * *systemd* is the default system initialisation mechanism in RHEL 8. It is the first process that starts at boot and it is the last process that terminates at shutdown.

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

    * Press *e* at the GRUB2 menu and add "rd.break" in place of "ro crash". This boot option tells the boot sequence to stop while the system is still using initramfs so that we can access the emergency shell.
    
    * Press *Ctrl+x* to reboot.
    
    * Run the following command to remount the */sysroot* directory with rw privileges:
        ```shell
        mount -o remount,rw /sysroot
        ```
    *  Run the following command to change the root directory to */sysroot*:
        ```shell
        chroot /sysroot
        ```
    *  Run *passwd* command to change the root password.
    
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

    * In RHEL logs capture messages generated by the kernel, daemons, commands, user activities, applications and other events. The daemon that is responsible for system logging is called *rsyslogd*. The configuration file for *rsyslogd* is in the */etc/rsyslog.conf* file. As defined in this configuration file, the default repository for most logs is the */var/log* directory.

    * The below commands can be used to start and stop the daemon:
        ```shell   
        systemctl stop rsyslog
        systemctl start rsyslog
        ```
    * A script called *logrotate* in */etc/cron.daily* invokes the *logrotate* command to rotate log files as per the configuration file.

    * The boot log file is available at */var/log/boot.log* and contains logs generated during system startup. The system log file is available in */var/log/messages* and is the default location for storing most system activities.

1. Preserve system journals

    * In addition to system logging, the *journald* daemon (which is an element of *systemd*) also collects and manages log messages from the kernel and daemon processes. It also captures system logs and RAM disk messages, and any alerts generated during the early boot stage. It stores these messages in binary format in files called *journals* in the */var/run/journal* directory. These files are structured and indexed for faster and easier searches, and can be viewed and managed using the *journalctl* command.

    * By default, journals are stored temporarily in the */run/log/journal* directory. This is a memory-based virtual file system and does not persist across reboots. To have journal files stored persistantly in */var/log/journal* the following commands can be run:
        ```shell   
        mkdir -p /var/log/journal
        systemctl restart systemd-journald
        ```

1. Start, stop, and check the status of network services

    * The *sshd* daemon manages ssh connections to the server. To check the status of this service:
        ```shell   
        systemctl is-active sshd        
        systemctl status sshd
        ```

    * To start and stop this service:
        ```shell   
        systemctl start sshd
        systemctl stop sshd
        ```

    * To enable or disable this service:
        ```shell      
        systemctl enable sshd
        systemctl disable sshd
        ```

    * To completely disable the service (i.e. to avoid loading the service at all):
        ```shell   
        systemctl mask sshd
        systemctl unmask sshd
        ```

1. Securely transfer files between systems

    * To transfer a file using the Secure Copy Protocol (SCP):
        ```shell   
        scp <file> <user>@<ip>:<file>
        ```

    * To transfer a directory:
        ```shell   
        scp /etc/ssh/* <user>@<ip>:/tmp
        ```

    * The direction of transfer can also be reversed:
        ```shell   
        scp <user>@<ip>:/tmp/sshd_config sshd_config_external
        ```

### Configure local storage

1. List, create, delete partitions on MBR and GPT disks

    * Data is stored on disk dives that are logically divided into partitions. A partition can exist on a portion of a disk, an entire disk, or across multiple disks. Each partition can contain a file system, raw data space, swap space, or dump space.

    * A disk in RHEL can be divided into several partitions. This partition information is stored on the disk in a small region, which is read by the operating system at boot time. This is known as the Master Boot Record (MBR) on BIOS-based systems, and GUID Partition Table (GPT) on UEFI-based systems. At system boot, the BIOS/UEFI scans all storage devices, detects the presence of MBR/GPT, identifies the boot disks, loads the boot loader program in memory from the default boot disk, executes the boot code to read the partition table and identify the */boot* partition, and continues with the boot process by loiading the kernel in the memory and passing control over to it.

    * MBR allows the creation of only up to 4 primary partitions on a single disk, with the option of using one of the 4 partitions as an extended partition to hold an arbitrary number of logical partitions. MBR also lacks addressing space beyond 2TB due to its 32-bit nature and the disk sector size of 512-byte that it uses. MBR is also non-redundant, so a system becomes unbootable if it becomes corrupted somehow.

    * GPT is a newer 64-bit partitioning standard developed and integrated to UEFI firmware. GPT allows for 128 partitions, use of disks much larger than 2TB, and redundant locations for the storage of partition information. GPT also allows a BIOS-based system to boot from a GPT disk, using the boot loader program stored in a protective MBR at the first disk sector.

    * To list the mount points, size and available space:
        ```shell   
        df -h
        ```

    * In RHEL block devices are an abstraction for certain hardware, such hard disks. The *blkid* command lists all block devices. The *lsblk* command lists more details about block devices.

    * To list all disks and partitions:
        ```shell   
        fdisk -l # MBR
        gdisk -l # GPT
        ```

    * For MBR based partitions the *fdisk* utilty can be used to create and delete partitions. To make a change to a disk:
        ```shell   
        fdisk <disk>
        ```

    * For GPT based partitions the *gdisk* utilty can be used to create and delete partitions. To make a change to a disk:
        ```shell   
        gdisk <disk>
        ```

    * To inform the OS of partition table changes:
        ```shell   
        partprobe
        ```
    
1. Create and remove physical volumes

    * Logical Volume Manager (LVM) is used to provide an abstraction layer between the physical storage and the file system. This enables the file system to be resized, to span across multiple physical disks, use random disk space, etc. One or more partitions or disks (physical volumes) can form a logical container (volume group), which is then divided into logical partitions (called logical volumes). These are further divided into physical extents (PEs) and logical extents (LEs).

    * A physical volume (PV) is created when a block storage device is brought under LVM control after going through the initialisation process. This process constructs LVM data structures on the device, including a label on the second sector and metadata information. The label includes a UUID, device size, and pointers to the locations of data and metadata areas.

    * A volume group (VG) is created when at least one physical volume is added to it. The space from all physical volumes in a volume group is aggregated to form one large pool of storage, which is then used to build one or more logical volumes. LVM writes metadata information for the volume group on each physical volume that is added to it.

    * To view physical volumes:
        ```shell   
        pvs
        ```

    * To view physical volumes with additional details:
        ```shell   
        pvdisplay
        ```

    * To initialise a disk or partition for use by LVM:
        ```shell   
        pvcreate <disk>
        ```

    * To remove a physical volume from a disk:
        ```shell   
        pvremove <disk>
        ```

1. Assign physical volumes to volume groups

    * To view volume groups:
        ```shell   
        vgs
        ```

    * To view volume groups with additional details:
        ```shell   
        vgdisplay
        ```

    * To create a volume group:
        ```shell   
        vgcreate <name> <disk>
        ```

    * To extend an existing volume group:
        ```shell   
        vgextend <name> <disk>
        ```

    * To remove a disk from a volume group:
        ```shell   
        vgreduce <name> <disk>
        ```

    * To remove the last disk from a volume group:
        ```shell   
        vgremove <name> <disk>
        ```

1. Create and delete logical volumes

    * To view logical volumes:
        ```shell   
        lvs
        ```

    * To view logical volumes with additional details:
        ```shell   
        lvdisplay
        ```

    * To create a logical volume in vg1 named lv1 and with 4GB of space:
        ```shell   
        lvcreate -L 4G -n lv1 vg1 
        ```

    * To extend the logical volume by 1GB:
        ```shell   
        lvextend -L+1G <lvpath>
        ```

    * To extend the logical volume by 1GB:
        ```shell   
        lvextend -L+1G <lvpath>
        ```

    * To reduce the size for a logical volume by 1GB:
        ```shell   
        lvreduce -L-1G <lvpath>
        ```

    * To remove a logical volume:
        ```shell   
        umount <mountpoint>
        lvremove <lvpath>
        ```

1. Configure systems to mount file systems at boot by universally unique ID (UUID) or label
    
    * The */etc/fstab* file is a system configuration file that lists all available disks, disk partitions and their options. Each file system is described on a separate line. The */etc/fstab* file is used by the *mount* command, which reads the file to determine which options should be used when mounting the specific device. A file system can be added to this file so that it is mounted on boot automatically.
    
    * The *e2label* command can be used to change the label on ext file systems. This can then be used instead of the UUID.
    
1. Add new partitions and logical volumes, and swap to a system non-destructively

    * Virtual memory is equal to RAM plus swap space. A swap partition is a standard disk partition that is designated as swap space by the *mkswap* command. A file can also be used as swap space but that is not recommended.

    * To create a swap:
        ```shell   
        mkswap <device>
        ```

    * To enable a swap:
        ```shell   
        swapon <device>
        ```

    * To check the status of swaps:
        ```shell   
        swapon -s
        ```

    * To disable a swap:
        ```shell   
        swapoff <device>
        ```

    * The */etc/fstab* file will need a new entry for the swap so that it is created persistently.

### Create and configure file systems

1. Create, mount, unmount, and use vfat, ext4, and xfs file systems

    * A file system is a logical container that is used to store files and directories. Each file system must be connected to the root of the directory hierarchy in order to be accessible. This is typically done automatically on system boot, but can be done manually as well. Each file system can be mounted or unmounted using the UUID associated with it or by using a label that can be assigned to it. Mounting is the process of attaching an additional filesystem, which resides on a CDROM, hard disk drive (HDD) or other storage device, to the currently accessible filesystem of a computer. 

    * Each file system is created in a separate partition or logical volume. A typical RHEL system has numerous file systems. During OS installation, the */* and */boot* file systems are created by default. Typical additional file systems created during installation include */home*, */opt*, */tmp*, */usr* and */var*.

    * File systems supported in RHEL are categorised as disk-based, network-based, and memory-based. Disk-based and network-based file systems are stored persistently, while data in memory-based systems is lost at system reboot. The different file systems are shown below:

    | File System          | Type    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    |----------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | ext2                 | Disk    | The second generation of the extended file system. The first generation is no longer supported. ext2 is deprecated in RHEL and will be removed in a future RHEL release.                                                                                                                                                                                                                                                                                                                                        |
    | ext3                 | Disk    | The third generation of the extended file system. It supports metadata journaling for faster recovery, superior reliability, file systems up to 16TB, files up to 2TB, and up to 32,000 sub-directories. ext3 writes each metadata update in its entirety to the journal after it has been completed. The system looks in the file system journal following a reboot after a system crash has occured, and recovers the file system rapidly using the updated structural information stored in its journal. |
    | ext4                 | Disk    | The fourth generation of the extended file system. It supports file systems up to 1EB, files up to 16TB, an unlimited number of sub-directories, metadata and quota journaling, and extended user attributes.                                                                                                                                                                                                                                                                                                   |
    | xfs                  | Disk    | XFS is a highly scalable and high-performance 64-bit file system.  It supports metadata journaling for faster crash recovery, online defragmentation, expansion quota journaling, and extended user attributes. It supports file systems and files of sizes up to 8EB. It is the default file system in RHEL 8.                                                                                                                                                                                                  |
    | btrfs                | Disk    | B-tree file system that supports a system size of 50TB. It supports more files, larger files, and larger volumes than ext4 and supports snapshotting and compression capabilities.                                                                                                                                                                                                                                                                                                                              |
    | vfat                 | Disk    | This is used for post-Windows 95 file system format on hard disks, USB drives, and floppy disks.                                                                                                                                                                                                                                                                                                                                                                                                                |
    | iso9660              | Disk    | This is used for CD/DVD-based optical file systems.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | BIOS Boot            | Disk    | A very small partition required for booting a device with a GUID partition table (GPT) on a BIOS system.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | EFI System Partition | Disk    | A small partition required for booting a device with a GUID partition table (GPT) on a UEFI system.                                                                                                                                                                                                                                                                                                                                                                                                             |
    | NFS                  | Network | A directory or file system shared over the network for access by other Linux systems.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | AutoFS               | Network | An NFS file system set to mount and unmount automatically on a remote system.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | CIFS                 | Network | Common Internet File System (a.k.a Samba). A directory or file system shared over the network for access by Windows and other Linux systems.                                                                                                                                                                                                                                                                                                                                                                    |

    * The *mount* command is used to attach a file system to a desired point in the directory heirarchy to make it accessible to users and applications. This point is referred to as the *mount point*, which is essentially an empty directory created soley for this point. The *mount* command requires the absolute pathname (or its UUID or label) to the block device containing the file system, and a mount point name in order to attach it to the directory tree. The *mount* command adds an entry to the */proc/mounts* file and instructs the kernel to add the entry to the */proc/mounts* file as well after a file system has been successfully mounted.

    * The opposite of the *mount* command is *unmount*, whihc is used to detach a file system from the directory hierarchy and make it inaccessible to users and applications.

    * To create a vfat file system:
        ```shell   
        mkfs.vfat <path>
        ```

    * To mount a vfat file system:
        ```shell   
        mount <path> /mnt
        ```

     * To unmount a vfat file system:
        ```shell   
        umount <path> /mnt
        ```

     * To check a vfat file system:
        ```shell   
        fsck.vfat <path>
        ```

    * To create an ext4 file system:
        ```shell   
        mkfs.ext4 <path>
        ```

    * To mount an ext4 file system:
        ```shell   
        mount <path> /mnt
        ```

     * To unmount an ext4 file system:
        ```shell   
        umount <path> /mnt
        ```

     * To check an ext4 file system:
        ```shell   
        fsck <path>
        ```

     * To get additional details about an ext4 file system:
        ```shell   
        dumpe2fs <path>
        ```

    * To create a xfs file system:
        ```shell   
        mkfs.xfs <path>
        ```

    * To mount a xfs file system:
        ```shell   
        mount <path> /mnt
        ```

     * To unmount a xfs file system:
        ```shell   
        umount <path> /mnt
        ```

     * To check a xfs file system:
        ```shell   
        xfs_repair <path>
        ```

     * To get additional details about an xfs file system:
        ```shell   
        xfs_info <path>
        ```

    * The path is the device name or a regular file that shall contain the file system.

1. Mount and unmount network file systems using NFS

     * To confirm nfs-utils is installed:
        ```shell   
        dnf install nfs-utils
        ```

     * To mount the network file system:
        ```shell   
        mount -t nfs 10.0.2.5:/home/nfs-share /mnt
        ```

     * Alternatively the following can be run after adding the entry to */etc/fstab*:
        ```shell   
        mount -a 
        ```

     * To unmount the network file system:
        ```shell   
        umount /mnt
        ```

1. Extend existing logical volumes

     * To extend the logical volume size by 2GB:
        ```shell   
        lvextend -L+2G /dev/vg1/lv1
        lvdisplay # confirm changes
        ```

     * To extend the file system:
        ```shell   
        df -Th # confirm file system type
        resize2fs /dev/vg1/lvl1 # for ext3 or ext4
        xfs_growfs /mnt # for xfs
        ```

1. Create and configure set-GID directories for collaboration

     * SUID (meaning set user id) is used to specify that a user can run an executable file with effective permissions of the file owner.  This is primarily used to elevate the privileges of the current user. When a user executes the file, the operating system will execute as the file owner. Instead of the normal *x* which represents execute permissions, an *s* will be visible. To set the SUID:
        ```shell
        chmod u+s <filename>
        ```
     
     * SGID (meaning set group id) is used to specify that a user can run an executable file with effective permissions of the owning group.  When a user executes the file, the operating system will execute as the owning group. Instead of the normal x Instead of the normal x which represents execute permissions, an s will be visible. To set the SGID:
        ```shell
        chmod g+s <filename>
        ```
    
     * To create a group and shared directory:
        ```shell
        groupadd accounts
        mkdir -p /home/shared/accounts
        chown nobody:accounts /home/shared/accounts
        chmod g+s /home/shared/accounts
        chmod 070 /home/shared/accounts
        ```

     * When using SGID on a directory all files that are created in the directory will be owned by the group of the directory as opposed to the group of the owner.

     * If the sticky bit is set on a directory, the files in that directory can only be removed by the owner. A typical use case is for the */tmp* directory. It can be written to by any user, but other users cannot delete the files of others. To set the sticky bit:
        ```shell
        chmod +t <directory>
        ```

    * The SUID, SGID and sticky bit can also be set with number notation. The standard number (rwx) is prepended with 4 for SUID, 2 for SGID, and 1 for the sticky bit.

    * To remove special permissions the *-* flag is used instead of the *+* flag.
     
1. Configure disk compression

    * The Virtual Data Optimiser (VDO) provides data reduction in the form of deduplication, compression, and thin provisioning.

    * To install vdo:
        ```shell
        dnf install vdo kmod-kvdo
        ```

    * To create the vdo:
        ```shell
        vdo create --name=vdo1 --device=/dev/sdb --vdoLogicalSize=30G --writePolicy=async
        ```

    * To create and mount the file system:
        ```shell
        mkfs.xfs /dev/mapper/vdo1
        mount /dev/mapper/vdo1 /mnt
        ```

1. Manage layered storage

    * Stratis is a storage management solution introduced in RHEL 8 that allows the configuration of advanced storage features such as pool-based management, thin provisioning, file system snapshots and monitoring.

    * To install stratis:
        ```shell
        dnf install stratisd stratis-cli
        systemctl start stratisd
        ```

    * To confirm there is no file system on the disk to be used:
        ```shell
        lsblk
        blkid -p /dev/sdb
        ```

    * If there is a file system remove it using:
        ```shell
        wipefs -a /dev/sdb
        ```

    * To create a stratis pool and confirm:
        ```shell
        stratis pool create strat1 /dev/sdb
        stratis pool list
        ```

    * To create a file system and confirm:
        ```shell
        stratis fs create strat1 fs1
        stratis fs list
        ```

    * To mount the file system and confirm:
        ```shell
        mount /stratis/strat1/fs1 /mnt
        df -h
        # add to /etc/fstab to make it persistant
        ```

    * To add a disk to the stratis pool and confirm:
        ```shell
        stratis pool add-data strat1 /dev/sdc
        stratis pool list
        ```

    * To create a snapshot and confirm:
        ```shell
        stratis fs snapshot strat1 fs1 snapshot1
        stratis filesystem list strat1
        ```

    * To mount a snapshot:
        ```shell
        unmount /stratis/strat1/fs1
        mount /stratis/strat1/snapshot1 /mnt
        ```

    * To destroy a snapshot and confirm:
        ```shell
        unmount /stratis/strat1/snapshot1
        stratis filesystem destroy strat1 snapshot1
        stratis filesystem list
        ```

    * To remove a stratis filesystem and pool and confirm:
        ```shell
        stratis filesystem destroy strat1 fs1
        stratis filesystem list
        stratis pool destroy strat1
        stratis pool list
        ```

1. Diagnose and correct file permission problems

    * File permissions can be modified using *chmod* and *setfacl*.
    
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

    * To check the status of a service:
        ```shell
        systemctl status <service>
        ```

    * To start a service:
        ```shell
        systemctl start <service>
        ```

    * To stop a service:
        ```shell
        systemctl stop <service>
        ```

    * To make a service reload its configuration:
        ```shell
        systemctl reload <service>
        ```

    * To make a service reload its configuration or restart if it can't reload:
        ```shell
        systemctl reload-or-restart <service>
        ```

    * To make a service start on boot:
        ```shell
        systemctl enable <service>
        ```

    * To stop a service starting on boot:
        ```shell
        systemctl disable <service>
        ```

    * To check if a service is enabled:
        ```shell
        systemctl is-enabled <service>
        ```

    * To check if a service has failed:
        ```shell
        systemctl is-failed <service>
        ```

    * To view the configuration file for a service:
        ```shell
        systemctl cat /usr/lib/sysdtemd/system/<service>
        ```

   * To view the dependencies for a service:
        ```shell
        systemctl list-dependencies <service>
        ```

   * To stop a service from being run by anyone but the system and from being started on boot:
        ```shell
        systemctl mask <service>
        ```

   * To remove a mask:
        ```shell
        systemctl unmask <service>
        ```

1. Configure systems to boot into a specific target automatically

   * To get the default target:
        ```shell
        systemctl get-default
        ```

   * To list available targets:
        ```shell
        systemctl list-units --type target --all
        ```

   * To change the default target:
        ```shell
        systemctl set-default <target>
        ```

    * The change will take affect after a reboot.

1. Configure time service clients

    * To print the date:
        ```shell
        date +%d%m%y-%H%M%S
        ```

    * To set the system clock as per the hardware clock:
        ```shell
        hwclock -s
        ```

    * To set the hardware clock as per the system clock:
        ```shell
        hwclock -w
        ```

    * The *timedatectl* command can also be used to view the date and time.

    * To change the date or time:
        ```shell
        timedatectl set-time 2020-03-18
        timedatectl set-time 22:43:00
        ```

    * To view a list of timezones:
        ```shell
        timedatectl list-timezones
        ```

    * To change the timezone:
        ```shell
        timedatectl set-timezone <timezone>
        ```

    * To enable NTP:
        ```shell
        timedatectl set-ntp yes
        ```

    * To start the *chronyd* service:
        ```shell
        systemctl start chronyd
        ```

1. Install and update software packages from Red Hat Network, a remote repository, or from the local file system

    * The .rpm extension is a format for files that are manipulated by the Redhat Package Manager (RPM) package management system. RHEL 8 provides tools for the installation and administration of RPM packages. A package is a group of files organised in a directory structure and metadata that makes up a software application.

    * An RPM package name follows the below format:
        ```shell
        openssl-1.0.1e-34.el7.x86_64.rpm
        # package name = openssl
        # package version = 1.0.1e
        # package release = 34
        # RHEL version = el7
        # processor architecture = x86_64
        # extension = .rpm
        ```

    * The *subscription-manager* command can be used to link a Red Hat subscription to a system.

    * The *dnf* command is the front-end to *rpm* and is the preferred tool for package management. The *yum* command has been superseded by *dnf* in RHEL 8. It requires that the system has access to a software repository. The primary benefit of *dnf* is that it automatically resolves dependencies by downloading and installaing any additional required packages.

    * To list enabled and disabled repositories:
        ```shell
        dnf repolist all
        dnf repoinfo
        ```
    
    * To search for a package:
        ```shell
        dnf search <package>
        dnf list <package>
        ```
    
    * To view more information about a particular package:
        ```shell
        dnf info <package>
        ```

    * To install a package:
        ```shell
        dnf install <package>
        ```

    * To remove a package:
        ```shell
        dnf remove <package>
        ```

    * To find a package from a file:
        ```shell
        dnf provides <path>
        ```

    * To install a package locally:
        ```shell
        dnf localinstall <path>
        ```

    * To view available groups:
        ```shell
        dnf groups list
        ```

    * To install a group (e.g. System Tools)
        ```shell
        dnf group "System Tools"
        ```

    * To remove a group (e.g. System Tools)
        ```shell
        dnf group remove "System Tools"
        ```

    * To see the history of installations using *dnf*:
        ```shell
        dnf history list
        ```

    * To undo a particular installation (e.g. ID=22):
        ```shell
        dnf history undo 22
        ```

    * To redo a particular installation (e.g. ID=22):
        ```shell
        dnf history redo 22
        ```

    * To add a repository using the dnf config manager:
        ```shell
        dnf config-manager --add-repo <url>
        ```

    * To enable a repository using the dnf config manager:
        ```shell
        dnf config-manager --enablerepo <repository>
        ```

    * To disable a repository using the dnf config manager:
        ```shell
        dnf config-manager --disablerepo <repository>
        ```

    * To create a repository:
        ```shell
        dnf install createrepo
        mkdir <path>
        createrepo --<name> <path>
        yum-config-manager --add-repo file://<path>
        ```

1. Work with package module streams

    * RHEL 8 introduced the concept of Application Streams. Components made available as Application Streams can be packaged as modules or RPM packages and are delivered through the AppStream repository in RHEL 8. Module streams represent versions of the Application Stream components. Only one module stream can be active at a particular time, but it allows multiple different versions to be available in the same dnf repository.
    
    * To view modules:
        ```shell
        dnf module list
        ```

    * To get information about a module: 
        ```shell
        dnf module info --profile <module-name>
        ```

    * To install a module: 
        ```shell
        dnf module install <module-name>
        ```

    * To remove a module: 
        ```shell
        dnf module remove <module-name>
        ```

    * To reset a module after removing it: 
        ```shell
        dnf module reset <module-name>
        ```

    * To be specific about the module installation:
        ```shell
        dnf module install <module-name>:<version>/<profile>
        ```

    * To check the version of a module:
        ```shell
        <module-name> -v
        ```

1. Modify the system bootloader

    * The GRUB2 configuration can be edited directly on the boot screen. The configuration can also be edited using the command line.

    * To view the grub2 commands: 
        ```shell
        grub2
        ```

    * To make a change to the configuration: 
        ```shell
        vi /etc/default/grub
        # Change a value
        grub2-mkconfig -o /boot/grub2/grub.cfg
        # View changes
        vi /boot/grub2/grub.cfg
        ```

### Manage basic networking

1. Configure IPv4 and IPv6 addresses

    * The format of an IPv4 address is a set of 4 8 bit integers that gives a 32 bit IP address.  The format of an IPv6 is a set of 8 16 bit hexadecimal numbers that gives a 128 bit IP address.

    * The *nmcli* command is used to configure networking using the NetworkManager service. This command is used to create, display, edit, delete, activate and deactive network connections. Each network device corresponds to a Network Manager device.

    * Using nmcli with the connection option lists the available connection profiles in NetworkManager.

    * The *ip* command can also be used for network configuration. The main difference between ip and nmcli is that changes made with the ip command are not persistent.
    
    * To view system IP addresses:
        ```shell
        ip addr
        ```

    * To show the current connections:
        ```shell
        nmcli connection show
        ```

    * Using nmcli with the device option lists the available network devices in the system.

    * To view the current network device status and details:
        ```shell
        nmcli device status
        nmcli device show
        ```

    * To add an ethernet IPv4 connection:
        ```shell
        nmcli connection add con-name <name> ifname <name> type ethernet ip4 <address> gw4 <address>
        ```

    * To manually modify a connection:
        ```shell
        nmcli connection modify <name> ipv4.addresses <address>
        nmcli connection modify <name> ipv4.method manual
        ```

    * To delete a connection:
        ```shell
        nmcli connection delete <name>
        ```

    * To activate a connection:
        ```shell
        nmcli connection up <name>
        ```

    * To deactivate a connection:
        ```shell
        nmcli connection down <name>
        ```

    * To check the DNS servers that are being used:
        ```shell
        cat /etc/resolv.conf
        ```

    * To change the DNS server being used:
        ```shell
        nmcli con mod <name> ipv4.dns <dns>
        systemctl restart network
        ```
   
1. Configure hostname resolution

    * To lookup the IP address based on a host name the *host* or *nslookup* commands can be used.

    * The */etc/hosts* file is like a local DNS. The */etc/nsswitch.conf* file controls the order that resources are checked for resolution. 

    * To lookup the hostname:
        ```shell
        hostname -s # short
        hostname -f # fully qualified domain name
        ```

    * The hostname file is located in */etc/hostname*. To refresh any changes run the *hostnamectl* command.

1. Configure network services to start automatically at boot

    * To install a service and make it start automatically at boot:
        ```shell
        dnf install httpd
        systemctl enable httpd
        ```
    
    * To set a connection to be enabled on boot:
        ```shell
        nmcli connection modify eth0 connection.autoconnect yes
        ```

1. Restrict network access using firewall-cmd/firewall

    * The default firewall system in RHEL 8 is *firewalld*. Firewalld is a zone-based firewall. Each zone can be associated with one or more network interfaces, and each zone can be configured to accept or deny services and ports. The *firewall-cmd* command is the command line client for firewalld.

    * To check firewall zones:
        ```shell
        firewall-cmd --get-zones
        ```

    * To list configuration for a zone:
        ```shell
        firewall-cmd --zone work --list-all
        ```

    * To create a new zone:
        ```shell
        firewall-cmd --new-zone servers --permanent
        ```

    * To reload firewall-cmd configuration:
        ```shell
        firewall-cmd --reload
        ```

    * To add a service to a zone:
        ```shell
        firewall-cmd --zone servers --add-service=ssh --permanent
        ```

    * To add an interface to a zone:
        ```shell
        firewall-cmd --change-interface=enp0s8 --zone=servers --permanent
        ```

    * To get active zones:
        ```shell
        firewall-cmd --get-active-zones
        ```

    * To set a default zone:
        ```shell
        firewall-cmd --set-default-zone=servers
        ```

    * To check the services allowed for a zone:
        ```shell
        firewall-cmd --get-services
        ```

    * To add a port to a zone:
        ```shell
        firewall-cmd --add-port 8080/tcp --permanent --zone servers
        ```

    * To remove a service from a zone:
        ```shell
        firewall-cmd --remove-service https --permanent --zone servers
        ```

    * To remove a port from a zone:
        ```shell
        firewall-cmd --remove-port 8080/tcp --permanent --zone servers
        ```

### Manage users and groups

1. Create, delete, and modify local user accounts

    * RHEL 8 supports three user account types: root, normal and service. The root user has full access to all services and administrative functions. A normal user can run applications and programs that they are authorised to execute. Service accounts are responsible for taking care of the installed services.

    * The */etc/passwd* file contains vital user login data.

    * The */etc/shadow* file is readable only by the root user and contains user authentication information. Each row in the file corresponds to one entry in the passwd file. The password expiry settings are defined in the */etc/login.defs* file.

    * The */etc/group* file contains the group information. Each row in the file stores one group entry.

    * The */etc/gshadow* file stores encrypted group passwords. Each row in the file corresponds to one entry in the group file.

    * Due to manual modification, inconsistencies may arise between the above four authentication files. The *pwck* command is used to check for inconsistancies.

    * The *vipw* and *vigr* commands are used to modify the *passwd* and *group* files respectively. These commands disable write access to these files while the privileged user is making the modifications.

    * To create a user:
        ```shell
        useradd user1
        ```
    
    * To check that the user has been created:
        ```shell
        cat /etc/group | grep user1
        ```

    * To specify the UID and GID at user creation:
        ```shell
        useradd -u 1010 -g 1005 user1
        ```

    * To create a user and add them to a group:
        ```shell
        useradd -G IT user 2
        ```

    * To delete a user:
        ```shell
        userdel user 1
        ```

    * To modify a user:
        ```shell 
        usermod -l user5 user1 # note that home directory will remain as user1
        ```

1. Change passwords and adjust password aging for local user accounts

    * To change the password for a user:
        ```shell 
        passwd user1
        ```

    * To step through password aging information the *chage* command can be used without any options.

    * To view user password expiry information:
        ```shell 
        chage -l user1
        ```

    * To set the password expiry for a user 30 days from now:
        ```shell 
        chage -M 30 user1
        ```

    * To set the password expiry date:
        ```shell 
        chage -E 2021-01-01 user1
        ```

    * To set the password to never expire:
        ```shell 
        chage -E -1 user1
        ```

1. Create, delete, and modify local groups and group memberships

    * To create a group:
        ```shell 
        groupadd IT
        ```

    * To create a group with a specific GID:
        ```shell 
        groupadd -g 3032
        ```

    * To delete a group:
        ```shell 
        groupdel IT
        ```

    * To modify the name of a group:
        ```shell 
        groupmod -n IT-Support IT
        ```

    * To modify the GID of a group:
        ```shell 
        groupmod -g 3033 IT-Support
        ```

    * To add a user to a group:
        ```shell 
        groupmod -aG IT-Support user1
        ```

    * To view the members of a group:
        ```shell 
        groupmems -l -g IT-Support
        ```

    * To remove a user from a group:
        ```shell 
        gpasswd -d user1 IT-Support
        ```

1. Configure superuser access

    * To view the sudoers file:
        ```shell 
        visudo /etc/sudoers
        ```

    * Members of the wheel group can use sudo on all commands. To add a user to the wheel group:
        ```shell 
        sudo usermod -aG wheel user1
        ```

    * To allow an individual user sudo access to specific commands:
        ```shell
        visudo /etc/sudoers
        user2 ALL=(root) /bin/ls, /bin/df -h, /bin/date
        ```

### Manage security

1. Configure firewall settings using firewall-cmd/firewalld

    * Network settings such as masquerading and IP forwarding can also be configured in the firewall-config GUI application. To install this application:
        ```shell
        dnf install firewall-config
        ```

    * To set port forwarding in the kernel setting:
        ```shell
        vi /etc/sysctl.conf
        # add line
        net.ipv4.ip_forward=1
        # save file
        sysctl -p
        ```

1. Create and use file access control lists

    * To give a user read and write access to a file using an access control list:
        ```shell
        setfacl -m u:user1:rw- testFile
        getfacl testFile
        ```

    * To remove an access control list for a user:
        ```shell
        setfacl -x u:user1 testFile
        getfacl testFile
        ```

    * To give a group read and execute access to a directory recursively using an access control list:
        ```shell
        setfacl -R -m g:IT-Support:r-x testDirectory
        getfacl testFile
        ```

    * To remove an access control list for a group:
        ```shell
        setfacl -x g:IT-Support testDirectory
        getfacl testFile
        ```

1. Configure key-based authentication for SSH

    * To generate an id_rsa and id_rsa.pub files:
        ```shell
        ssh-keygen
        ```
    * To enable ssh for a user:
        ```shell
        touch authorized_keys
        echo "publicKey" > /home/new_user/.ssh/authorized_keys
        ```

    * To copy the public key from server1 to server2:
        ```shell
        ssh-copy-id -i ~/.ssh/id_rsa.pub server2
        cat ~/.ssh/known_hosts # validate from server1
        ```

1. Set enforcing and permissive modes for SELinux

    * Security Enhanced Linux (SELinux) is an implementation of Mandatory Access Control (MAC) architecture developed by the U.S National Security Agency (NSA). MAC provides an added layer of protection beyond the standard LInux Discretionary Access Control (DAC), which includes the traditional file and directory permissions, ACL settings, setuid/setgid bit settings, su/sudo privileges etc.

    * MAC controls are fine-grained; they protect other services in the event one of the services is negotiated. MAC uses a set of defined authorisation rules called policy to examine security attributes assocaited with subjects and objects when a subject tries to access an object, and decides whether or not to permit this access attempt. SELinux decisions are stored in a special cache referred to as Access Vector Cache (AVC).

    * When an application or process makes a request to access an object, SELinux checks with the AVC, where permissions are cached for subjects and objects. If a decision is unable to be made, it sends the request to the security server. The security server checks for the security context of the app or process and the object. Security context is applied from the SELinux policy database. 

    * To check the SELinux status:
        ```shell
        getenforce
        sestatus
        ```

    * To put SELinux into permissive mode modify the */etc/selinux/config* file as per the below and reboot:
        ```shell
        SELINUX=permissive
        ```

    * Messages logged from SELinux are available in */var/log/messages*.

1. List and identify SELinux file and process context

    * To view the SELinux contexts for files:
        ```shell
        ls -Z
        ```

    * To view the contexts for a user:
        ```shell
        id -Z
        ```
    * The contexts shown follow the user:role:type:level syntax. The SELinux user is mapped to a Linux user using the SELinux policy. The role is an intermediary between domains and SELinux users. The type defines a domain for processes, and a type for files. The level is used for Multi-Category Security (MCS) and Multi-Level Security (MLS).

    * To view the processes for a user:
        ```shell
        ps -Z # ps -Zaux to see additional information
        ```

1. Restore default file contexts

    * To view the SELinux contexts for files:
        ```shell
        chcon unconfined:u:object_r:tmp_t:s0
        ```

    * To restore the SELinux contexts for a file:
        ```shell
        restorecon file.txt
        ```

    * To restore the SELinux contexts recursively for a directory:
        ```shell
        restorecon -R directory
        ```

1. Use boolean settings to modify system SELinux settings

    * SELinux has a large number of contexts and policies already defined. Booleans within SELinux allow common rules to be turned on and off.

    * To check a SELinux boolean setting:  
        ```shell
        getsebool -a | grep virtualbox
        ```

    * To set a SELinux boolean setting permanently:  
        ```shell
       setsebool -P use_virtualbox on
        ```

1. Diagnose and address routine SELinux policy violations

    * The SELinux Administration tool is a graphical tool that enables a number of configuration and management operations to be performed. To install and run the tool:
       ```shell
       yum install setools-gui
       yum install policycoreutils-gui
       system-config-selinux
       ```

    * SELinux alerts are written to */var/log/audit/audit.log* if the *auditd* daemon is running, or to the */var/log/messages* file via the *rsyslog* daemon in the absence of *auditd*.

    * A GUI called the SELinux Troubleshooter can be accessed using the *sealert* command. This allows SELinux denial messages to be analysed and provides recommendations on how to fix issues.

### Exercises

1. Recovery and Practise Tasks

    * Recover the system and fix repositories:
        ```shell
        # press e at grub menu
        rd.break # add to line starting with "linux16"
        # Replace line containing "BAD" with "x86_64"
        mount -o remount, rw /sysroot
        chroot /sysroot
        passwd
        touch /.autorelabel
        # reboot
        # reboot - will occur automaticaly after relabel (you can now login)
        grub2-mkconfig -o /boot/grub2/grub.cfg # fix grub config
        yum repolist all
        # change files in /etc/yum.repos.d to enable repository
        yum update -y
        # reboot
        ```

    * Add 3 new users alice, bob and charles. Create a marketing group and add these users to the group. Create a directory */marketing* and change the owner to alice and group to marketing. Set permissions so that members of the marketing group can share documents in the directory but nobody else can see them. Give charles read-only permission. Create an empty file in the directory: 
        ```shell
        useradd alice
        useradd bob
        useradd charles
        groupadd marketing
        mkdir /marketing
        usermod -aG marketing alice
        usermod -aG marketing bob
        usermod -aG marketing charles
        chgrp marketing marketing # may require restart to take effect
        chmod 770 marketing
        setfacl -m u:charles:r marketing
        setfacl -m g:marketing:-wx marketing
        touch file
        ```

    * Set the system timezone and configure the system to use NTP:
        ```shell
        yum install chrony
        systemctl enable chronyd.service
        systemctl start chronyd.service
        timedatectl set-timezone Australia/Sydney
        timedatectl set-ntp true
        ```

    * Install and enable the GNOME desktop:
        ```shell
        yum grouplist
        yum groupinstall "GNOME Desktop" -y
        systemtctl set-default graphical.target
        reboot
        ```

    * Configure the system to be an NFS client:
        ```shell
        yum install nfs-utils
        ```

    * Configure password aging for charles so his password expires in 60 days:
        ```shell
        chage -M 60 charles
        chage -l charles # to confirm result
        ```

    * Lock bobs account:
        ```shell
        passwd -l bob
        passwd --status bob # to confirm result
        ```

    * Find all setuid files on the system and save the list to /testresults/setuid.list:
        ```shell
        find / -perm /4000 > setuid.list
        ```

    * Find all setuid files on the system and save the list to /testresults/setuid.list:
        ```shell
        find / -perm /4000 > setuid.list
        ```

    * Set the system FQDN to *centos.local* and alias to *centos*:
        ```shell
        hostnamectl set-hostname centos --pretty
        hostnamectl set-hostname centos.local
        hostname -s # to confirm result
        hostname # to confirm result
        ```

    * As charles, create a once-off job that creates a file called */testresults/bob* containing the text "Hello World. This is Charles." in 2 days time:
        ```shell
        vi hello.sh
        # contents of hello.sh
        #####
        #!/bin/bash
        # echo "Hello World. This is Charles." > bob
        #####
        chmod 755 hello.sh
        usermod charles -U -e -- "" # for some reason the account was locked
        at now + 2 days -f /testresults/bob/hello.sh
        cd /var/spool/at # can check directory as root to confirm
        atq # check queued job as charles
        # atrm 1 # can remove the job using this command
        ```

    * As alice, create a periodic job that appends the current date to the file */testresults/alice* every 5 minutes every Sunday and Wednesday between the hours of 3am and 4am. Remove the ability of bob to create cron jobs:
        ```shell
        echo "bob" >> /etc/at.deny
        sudo -i -u alice
        vi addDate.sh
        # contents of hello.sh
        #####
        #!/bin/bash
        # date >> alice
        #####
        /testresults/alice/addDate.sh
        crontab -e
        # */5 03,04 * * sun,wed /testresults/alice/addDate.sh
        crontab -l # view crontab
        # crontab -r can remove the job using this command
        ```

    * Set the system SELinux mode to permissive:
        ```shell
        setstatus # confirm current mode is not permissive
        vi /etc/selinux/config # Update to permissive
        reboot
        setstatus # confirm current mode is permissive
        ```

    * Set the system SELinux mode to permissive:
        ```shell
        setstatus # confirm current mode is not permissive
        vi /etc/selinux/config # Update to permissive
        reboot
        setstatus # confirm current mode is permissive
        ```

    * Create a firewall rule to drop all traffic from 10.10.10.*:
        ```shell
        firewall-cmd --zone=drop --add-source 10.10.10.0/24
        firewall-cmd --list-all --zone=drop # confirm rule is added
        firewall-cmd --permanent --add-source 10.10.10.0/24
        reboot
        firewall-cmd --list-all --zone=drop # confirm rule remains
        ```

1. Linux Academy - Using SSH, Redirection, and Permissions in Linux

    * Enable SSH to connect without a password from the dev user on server1 to the dev user on server2:
        ```shell
        ssh dev@3.85.167.210
        ssh-keygen # created in /home/dev/.ssh
        ssh-copy-id 34.204.14.34
        ```    

    * Copy all tar files from `/home/dev/` on server1 to `/home/dev/` on server2, and extract them making sure the output is redirected to `/home/dev/tar-output.log`:
        ```shell
        scp *.tar* dev@34.204.14.34:/home/dev
        tar xfz deploy_script.tar.gz > tar-output.log
        tar xfz deploy_content.tar.gz >> tar-output.log
        ```
    
    * Set the umask so that new files are only readable and writeable by the owner:
        ```shell
        umask 0066 # default is 0666, subtract 0066 to get 0600
        ```

    * Verify the `/home/dev/deploy.sh` script is executable and run it:
        ```shell
        chmod 711 deploy.sh
        ./deploy.sh
        ```

1. Linux Academy - Storage Management

    * Create a 2GB GPT Partition:
        ```shell
        lsblk # observe nvme1n1 disk
        sudo gdisk /dev/nvme1n1
        # enter n for new partition
        # accept default partition number
        # accept default starting sector
        # for the ending sector, enter +2G to create a 2GB partition
        # accept default partition type
        # enter w to write the partition information
        # enter y to proceed
        lsblk # observe nvme1n1 now has partition
        partprobe # inform OS of partition change
        ```

    * Create a 2GB MBR Partition:
        ```shell
        lsblk # observe nvme2n1 disk
        sudo fdisk /dev/nvme2n1
        # enter n for new partition
        # accept default partition type
        # accept default partition number
        # accept default first sector
        # for the ending sector, enter +2G to create a 2GB partition
        # enter w to write the partition information
        ```

    * Format the GPT Partition with XFS and mount the device persistently:
        ```shell
        sudo mkfs.xfs /dev/nvme1n1p1
        sudo blkid # observe nvme1n1p1 UUID
        vi /etc/fstab
        # add a line with the new UUID and specify /mnt/gptxfs
        mkdir /mnt/gptxfs
        sudo mount -a
        mount # confirm that it's mounted
        ```

    * Format the MBR Partition with ext4 and mount the device persistently:
        ```shell
        sudo mkfs.ext4 /dev/nvme2n1p1
        mkdir /mnt/mbrext4
        mount /dev/nvme2n1p1 /mnt/mbrext4
        mount # confirm that it's mounted
        ```

1. Linux Academy - Working with LVM Storage

    * Create Physical Devices:
        ```shell
        lsblk # observe disks xvdf and xvdg
        pvcreate /dev/xvdf /dev/xvdg
        ```

    * Create Physical Devices:
        ```shell
        vgcreate RHCSA /dev/xvdf /dev/xvdg
        vgdisplay # view details
        ```

    * Create a Logical Volume:
        ```shell
        lvcreate -n pinehead -L 3G RHCSA
        lvdisplay # or lvs, to view details
        ```

    * Format the LV as XFS and mount it persistantly at `/mnt/lvol`:
        ```shell
        fdisk -l # get path for lv
        mkfs.xfs /dev/mapper/RHCSA-pinehead
        mkdir /mnt/lvol
        blkid # copy UUID for /dev/mapper/RHCSA-pinehead
        echo "UUID=76747796-dc33-4a99-8f33-58a4db9a2b59" >> /etc/fstab
        # add the path /mnt/vol and copy the other columns
        mount -a
        mount # confirm that it's mounted
        ```

    * Grow the mount point by 200MB:
        ```shell
        lvextend -L +200M /dev/RHCSA/pinehead
        ```

1. Linux Academy - Network File Systems

    * Set up a SAMBA share:
        ```shell
        # on the server
        yum install samba -y
        vi /etc/samba/smb.conf
        # add the below block
        #####
        #[share]
        #    browsable = yes
        #    path = /smb
        #    writeable = yes
        #####
        useradd shareuser
        smbpasswd -a shareuser # enter password
        mkdir /smb
        systemctl start smb
        chmod 777 /smb
        
        # on the client
        mkdir /mnt/smb
        yum install cifs-utils -y
        # on the server hostname -I shows private IP
        mount -t cifs //10.0.1.100/share /mnt/smb -o username=shareuser,password= # private ip used
        ```


    * Set up the NFS share:
        ```shell
        # on the server
        yum install nfs-utils -y
        mkdir /nfs
        echo "/nfs *(rw)" >> /etc/exports
        chmod 777 /nfs
        exportfs -a
        systemctl start {rpcbind,nfs-server,rpc-statd,nfs-idmapd}

        # on the client
        yum install nfs-utils -y
        mkdir /mnt/nfs
        showmount -e 10.0.1.101 # private ip used
        systemctl start rpcbind
        mount -t nfs 10.0.1.101:/nfs /mnt/nfs
        ```

1. Linux Academy - Maintaining Linux Systems

    * Schedule a job to update the server midnight tonight:
        ```shell
        echo "dnf update -y" > update.sh
        chmod +x update.sh
        at midnight -f update.sh
        atq # to verify that job is scheduled
        ```

    * Modify the NTP pools:
        ```shell
        vi /etc/chrony.conf
        # modify the lines at the top of the file
        ```

    * Modify GRUB to boot a different kernel:
        ```shell
        grubby --info=ALL # list installed kernels
        grubby --set-default-index=1
        grubby --default-index # verify it worked
        ```

1. Linux Academy - Managing Users in Linux

    * Create the superhero group:
        ```shell
        groupadd superhero
        ```

    * Add user accounts for Tony Stark, Diana Prince, and Carol Danvers and add them to the superhero group:
        ```shell
        useradd tstark -G superhero
        useradd cdanvers -G superhero
        useradd dprince -G superhero
        ```

    * Replace the primary group of Tony Stark with the wheel group:
        ```shell
        usermod tstark -aG wheel
        grep wheel /etc/group # to verify
        ```

    * Lock the account of Diana Prince:
        ```shell
        usermod -L dprince 
        chage dprince -E 0
        ```


1. Linux Academy - SELinux Learning Activity

    * Fix the SELinux permission on `/opt/website`:
        ```shell
        cd /var/www # the default root directory for a web server
        ls -Z # observe permission on html folder
        semanage fcontext -a -t httpd_sys_content_t '/opt/website(/.*)'
        restorecon /opt/website
        ```

    * Deploy the website and test:
        ```shell
        mv /root/index.html /opt/website
        curl localhost/index.html # receive connection refused response
        systemctl start httpd # need to start the service
        setenforce 0 # set to permissive to allow for now
        ```

    * Resolve the error when attempting to access `/opt/website`:
        ```shell
        ll -Z # notice website has admin_home_t
        restorecon /opt/website/index.html
        ```