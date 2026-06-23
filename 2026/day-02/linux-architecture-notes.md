**The core components of Linux (kernel, user space, init/systemd)**

Hardware: Physical devices like CPU, RAM, Disk and Network Devices.

Kernel : Core of Linux that manages processes, memory, devices and system resources.

User Space: Area where users and applications run.

Shell: Command Line Interface used to interact with kernel.

Systemd: First process (PID 1) responsible for managing services and system startups.


**Processes in Linux**

- A process is a running instance of program.

Examples:
  - nginx
  - sshd
  - docker
  - Python

\ -> Each process has a unique process ID (PID)

**common commands**

- ps aux
- top
- htop

**The core 5 Process states are:**

- Running (R): Process actively using CPU.
- Sleeping (S): Process is waiting for an event or resource.
- Stopped (T):  Process execution is paused.
- Zombie (Z): Process has completed execution but still exists in process table.

**What systemd does**
- Systemd is the core system manager in Linux.
- systemd is init system used by modern Linux distributions.
- Responsibilities:
- Starts services during Boot
- Manages system services
- Handle service failures
- Controls startup sequence

 systemctl start nginx
 systemctl stops nginx
 systemctl status nginx

**5 commands used daily**

ps -  View running processes
top - Monitor system resources in real time
systemctl - manages services
df -h - check disk usage
free -h - check memory usage

