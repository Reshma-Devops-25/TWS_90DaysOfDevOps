**Process Management**



ps - display running processes

ps aux - display all running processes

top - monitor processes in real time.

htop - interactive process monitoring tool

kill -9 PID - terminate process by PID

killall process\_name - Kill all process by name

pgrep process\_name - find process ID by name.



ps aux --sort=-%CPU | head - List processes consuming the most CPU

pstree -p - shows tree structure between running processes





**System Information**



hostname - display current hostname

date - Display todays date and time

cal - Display current month calendar

uptime - show current uptime

w - Display who is online

whoami - who are logged in as

uname -a - Show kernel information

cat /etc/os-release - Display system information and identification 

lnblk - show block devices in tree format

systemctl list-units --type=service --state=running  - Status of running services







**File system**



pwd  - Prints current working directory

ls -al - Long lists with hidden files

cd - change directory from one to another

mkdir -p file1 - Create directory 

rm file - remove file 

grep pattern file - search/find text in file

find - search for files and directories 

cp file1 file2 - copy file1 to file2

mv file1 file2 - rename or move from file1 to file1

awk '{print $1}' fiel - extract specific column 

sed 's/old/new' file - replace text from old to new





**Networking** 



ipconfig - Display current TCP/IP network configuration values of the system.

ping google.com - fetch pinged packets 

curl https://google.com - Test website response

dig google.com - DNS lookup

ip addr - show IP address for the current service



