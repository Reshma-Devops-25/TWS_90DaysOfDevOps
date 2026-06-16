The core components of Linux (kernel, user space, init/systemd)

Hardware : Physical devices CPU, RAM, Disk and Network devices.
Kernel : Core part of Linux that manages processes, memory, devices and system resources.
Shell : Command line interface used to interact with kernel.
User Space : Area where users and applications are run.
Systemd : First Process (PID 1) which manages services and system startups.


Processes in Linux
 - A process is a running instance of program.

  Examples:
	- nginx
	- sshd
        - docker
	- Python

- Each process has a unique process ID (PID)

common commands
 - ps aux
 - top
 - htop
 
The core 5 Process states are:

 - Running (R): Process actively using CPU.
 - Sleeping (S): Process is waiting for an event or resource.
 - Stopped (T):  Process execution is paused.
 - Zombie (Z): Process has completed execution but still exists in process table.
 
What systemd does

Systemd is a core system manager in Linux
Systemd is a init system used by Modern Linux distribution.
Responsibilities:
	- Starts services during boot
	- Manages system services
	- Handle service failure
	- Control startup sequence

systemctl start nginx
systemctl stop nginx
systemctl status nginx

5 Commands used daily

ps - view running processes
ps aux - display all running processes
df -h - check disk usage 
free -h - Check memory usage 
ls -al - Long list with hidden files