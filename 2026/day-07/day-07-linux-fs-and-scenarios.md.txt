 ### Linux File System Hierarchy and Scenario Based practice

- File System Hierarchy defines the directory structure and directory contents in Linux OS

**Core Directories (Must Know):**

`/` (root) 

- Root directory is the top most directory in Linux, No directory exists above the root directory.
- Its an parent directory for all other directories and root has permission to modify any directories.

Command:
pwd: I use this command to check present working directory
ls -l / : Used to see top-level structure of Linux system.


`/home` 

- Personal/home directories for each user.
- User specific files and folders will be stored here.

command:

ls -l /home

I use this to access or manage user files

 `/root` 

- Root user's home directory
- Home directory for administrator/root user.

command:

sudo ls -l /root 
 
I need to work with files owned by root/admin user

 `/etc` 

- Contains configuration files for entire system.

command:
cat /etc/passwd
cat /etc/group

I use this command to see users and groups information, here i can modify user and grp permissions

`/var/log` 

- Contains Log, mail and variables system data (very important for DevOps!)
- Impotent for debugging system issues.


`/tmp` 

- Temporary files are stored here. Not meant for permanent storage.
- Files may be deleted automatically and used by applications for temporary processing.

command:
ls -l /tmp

I need this to check any temporary files get created by any applications.


`/bin` 

- Essential user commands.
- It contains basic commands required for system operations and user tasks.
- commands such as ls, cd, mv, cp are available here. 

I would use this when: I want to know where important command binaries are stored.

	
 `/usr/bin` 

- User command binaries are stored here. Many commonly used programs are located here. 
- Most software installed  using package managers.

I would use when: I need to locate installed command-line tools.


`/opt` 

- Optional/third-party applications/Softwares are installed here.

I would use when: I need to to install external packages.


# Find the largest log file in /var/log 
du -sh /var/log/* 2>/dev/null | sort -h | tail -5

0       /var/log/wtmp
8.0K    /var/log/alternatives.log
28K     /var/log/apt
88K     /var/log/bootstrap.logls -
124K    /var/log/dpkg.log

- These are the top 5 heaviest consumers of disk space under /var/log.
- 2>/dev/null is a common trick to hide unwanted error messages, especially in scripts or one-liners where you only care about successful output.

Scenario: Check if a service is running

Question: How do you check if the 'nginx' service is running?


My Solution (Step by step):

Step 1: Check service status

systemctl status nginx

Why: It shows if the service is active, failed, or stopped

Step 2: View recent Nginx logs

journalctl -u nginx -n 20

Why: It displays recent logs and helps identify startup issues.

Step 3: Check if service is enabled on boot

systemctl is-enabled nginx

Why: To know if nginx will start automatically after reboot.

Step 4: Check if nginx is listening on port

sudo ss -tulpn | grep nginx

Why: It confirms that Nginx is running and accepting connections.

What I learned: Always check status first, then review logs and verify that service is listening on the expected port.

Scenario 2: High CPU Usage

Application server is running very slow and CPU utilization is very high.

Step 1:

top 

why: Monitor live CPU and memory usage.

Step 2:

ps aux --sort=%cpu | head -10

Why: Identify top 10 processes consuming highest CPU and memory resources.

Step 3:

pidof nginx

why: Find process ID of specific application.

Step 4:

top -p <PID>

Why: Monitor resource consumption of specific process.

What I learned: CPU bottlenecks can often be identified by checking top resource-consuming processes.

Scenario 3: Finding Service Logs

Developer wants to check docker service logs

Step 1:

systemctl status docker

Why: To check docker service is running correctly.

Step 2:

journalctl -u docker -n 50

Why: To view the latest docker service logs to identify warnings and errors.

Step 3:

journalctl -u docker -f

Why: Monitor docker logs in real time while troubleshooting issues.

What i learned: Systemd-managed services logs are stored in journal and can be accessed using journalctl command. Container specific logs can be viewed using the docker log command.

Scenario 4: File Permissions Issue

A script named backup.sh shows permission denied when executed

Step 1:

ls -l backup.sh

Why: To check current permissions assigned to the script.

Step 2:

chmod +x backup.sh

Why: To add/grant execute permission so that the script can be run.

Step 3:

ls -l backup.sh

Why: To verify that execute permission has been granted to script successfully.

Step 4:

./backup.sh

Why: Execute the script after granting permission. 





















































 

































































