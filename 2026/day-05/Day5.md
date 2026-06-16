**Environment basics:**



**uname -a**



Linux ip-172-31-21-180 7.0.0-1004-aws #4-Ubuntu SMP PREEMPT Mon Apr 13 13:14:24 UTC 2026 x86\_64 GNU/Linux



**Observation**: details of aws EC2 information

Kernel name: Linux

Hostname: ip-172-31-22-33

Kernel release: 5.15.0-1051-aws

Kernel version: #55-Ubuntu SMP Fri May 10 12:00:00 UTC 2024

Machine hardware name: x86\_64

Processor type: x86\_64

Hardware platform: x86\_64

Operating system: GNU/Linux





**lsb\_release -a**



No LSB modules are available.

Distributor ID: Ubuntu

Description:  Ubuntu 26.04 LTS

Release:  26.04

Codename: resolute



**Observation**: Linux distribution and version details



**cat /etc/os-release**



PRETTY\_NAME="Ubuntu 26.04 LTS"

NAME="Ubuntu"

VERSION\_ID="26.04"

VERSION="26.04 (Resolute Raccoon)"

VERSION\_CODENAME=resolute

ID=ubuntu

ID\_LIKE=debian

HOME\_URL="https://www.ubuntu.com/"

SUPPORT\_URL="https://help.ubuntu.com/"

BUG\_REPORT\_URL="https://bugs.launchpad.net/ubuntu/"

PRIVACY\_POLICY\_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"

UBUNTU\_CODENAME=resolute

LOGO=ubuntu-logo



**Observation** : Information about distribution ID, name, Version



**Filesystem sanity:**



create a throwaway folder and file



mkdir /tmp/runbook-demo



**Observation** : Temporary directory created succesfully





cp /etc/hosts /tmp/runbook-demo/hosts-copy \&\& ls -l /tmp/runbook-demo



**Observation** : Having read and write permission for user and read only permission for grp and others, contents are copied fron /etc/hosts to /tmp/runbook-demo





**CPU / Memory:**



ps -o pid,comm - Display process id and command

ps -o pcpu - Display CPU usage percentage for processes

ps -o pmem - Displays percentage of memory for each processes



**Observation** : Can see clearly usage percentage of CPU, memory and PID for processes



free -h -

&#x20;              total        used        free      shared  buff/cache   available

Mem:           951Mi       356Mi       212Mi       1.8Mi       514Mi       595Mi

Swap:             0B          0B          0B



**Observation** : Not consumed more memory.



**Disk / IO:**

df -h :  Displays disk space usage of mounted file systems in a human-readable format.



Filesystem      Size  Used Avail Use% Mounted on

/dev/root       6.7G  2.4G  4.3G  36% /



**Observation**: Root filesysten has used 36% memory



du -sh -



52K  .



**Observation** : exact disk space usage.

&#x20;

vmstat - displays snapshot of cpu, io memory



procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------

&#x20;r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu

&#x20;0  0      0 188524  48948 506164    0    0    32    63  216    0  0  0 100  0  0  0



**Observation**: Usage space actively free.





**Network:**



ss -tulpn



tcp               LISTEN             0                  5                                         127.0.0.1:44321

tcp               LISTEN             0                  5                                         127.0.0.1:4330



**Observation**: State of process along with IP address and port



curl -I localhost -





HTTP/1.1 200 OK

Server: nginx/1.28.3 (Ubuntu)



Obaservation: Nginx is serving request successfullytail



**Logs:**

journalctl -u nginx -n 5 - Status of ngix server for top 5 lines



Jun 12 07:41:12 ip-172-31-21-180 systemd\[1]: Starting nginx.service - A high performance web server and a reverse proxy server...

Jun 12 07:41:12 ip-172-31-21-180 systemd\[1]: Started nginx.service - A high performance web server and a reverse proxy server.

Jun 12 10:59:20 ip-172-31-21-180 systemd\[1]: Stopping nginx.service - A high performance web server and a reverse proxy server...

Jun 12 10:59:20 ip-172-31-21-180 systemd\[1]: nginx.service: Deactivated successfully.

Jun 12 10:59:20 ip-172-31-21-180 systemd\[1]: Stopped nginx.service - A high performance web server and a reverse proxy server.



Observation: Complete status of server nginx when it started, stopped, and so on



tail -n 10 /var/log/nginx/access.log



::1 - - \[12/Jun/2026:18:04:54 +0000] "HEAD / HTTP/1.1" 200 0 "-" "curl/8.18.0"



Observation: HTTP request has returned 200 status code

