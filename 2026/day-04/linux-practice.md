**Process management**

- ps aux -> Display all running process
- pgrep syslog -> Display ID of syslog proc

**Service commands**
- systemctl status -> Provide complete status of current system or service.
- systemctl list-path --all -> Lists all path units currently loaded on system.

**Log commands**
- journalctl -f -> follow live log entries.
- journalctl -u nginx -> logs for nginx service.
- head -n 10 /var/log/auth.log -> display first 10 line of log.
