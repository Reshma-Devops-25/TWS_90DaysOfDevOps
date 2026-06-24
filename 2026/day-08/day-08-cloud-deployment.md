Part 1: Launch Cloud Instance & SSH Access

Connect EC2 via SSH

ssh -i "Linux-Practice.pem" ubuntu@ec2-54-83-182-154.compute-1.amazonaws.com

Connected securely to ubuntu EC2 instance using SSH.

Part 2: Install Docker & Nginx

Step 1: Update System

sudo apt-get update -y

Updated package information using ubuntu repositories.


Step 2: Install Nginx

sudo apt install nginx -y


Successfully installed nginx service.


Step 3: Verify Nginx is running

systemctl status nginx

Checked that nginx service is running successfully

Step 4: Verify installed package

dpkg -l | grep nginx
dpkg -s nginx

Confirmed that nginx was installed and viewed package details.

Part 3: Security Group Configuration 

Opened browser: `http://54.83.182.154/`

Welcome to Nginx web page was shown on browser.

Part 4: Extract Nginx Logs 

Step 1: View Nginx Logs

 journalctl -u nginx -n -20

Viewed latest 20 log entries.

Step 2: Save Logs to File

 journalctl -u nginx -n 20 > ~/nginx-logs.txt
 
Saved logs in nginx-logs.txt file 

Step 3: Download Log File to Your Local Machine

scp -i "Linux-Practice.pem" ubuntu@ec2-54-83-182-154.compute-1.amazonaws.com>~/nginx-logs.txt .

Downloaded log file into my local machine successfully.

Challenges Faced

- SCP initially failed because the PEM file was not in my current directory.
- Not able to check installed package details.

Solution
- Navigated to the Downloads folder where the PEM file was stored.
- Used correct command to check installed package details.

What I Learned:

- How to create EC2 instance on AWS.
- How to connect to EC2 instance using SSH.
- How to check installed packages using command dpkg.
- How to view service logs using journalctl command.
- How to download file into my local machine using scp.
- Basic web deployment and log management.
