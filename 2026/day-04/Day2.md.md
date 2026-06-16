**The core components of Linux (kernel, user space, init/systemd)**



&#x20;  Hardware: Physical devices like CPU, RAM, Disk and Network Devices.

&#x20;  Kernel : Core of Linux that manages processes, memory, devices and system resources.

&#x20;  User Space: Area where users and applications run.

&#x20;  Shell: The user interface or Command Line Interface used to interact with kernel.

&#x20;  Systemd: First process (PID 1) responsible for managing services  and system startups.



**Processes in Linux**

&#x20;- A process is a running instance of program.



&#x20; Examples:

&#x09;- nginx

&#x09;- sshd

&#x20;       - docker

&#x09;- Python



\- Each process has a unique process ID (PID)



**common commands**

&#x20;- ps aux

&#x20;- top

&#x20;- htop

&#x09;

&#x20;

&#x20;**The core 5 Process states are:**



&#x20;- Running (R): Process actively using CPU.

&#x20;- Sleeping (S): Process is waiting for an event or resource.

&#x20;- Stopped (T):  Process execution is paused.

&#x20;- Zombie (Z): Process has completed execution but still exists in process table.

&#x20;



**What systemd does**



&#x20;- Systemd is the core system manager in Linux.

&#x20;- systemd is init system used by modern Linux distributions.

&#x20;- Responsibilities:

&#x09;- Starts services during Boot

&#x09;- Manages system services

&#x09;- Handle service failures

&#x09;- Controls startup sequence



&#x20; systemctl start nginx

&#x20; systemctl stops nginx

&#x20; systemctl status nginx

&#x20;

**5 commands used daily**



&#x20;ps -  View running processes

&#x20;top - Monitor system resources in real time

&#x20;systemctl - manages services

&#x20;df -h - check disk usage

&#x20;free -h - check memory usage

