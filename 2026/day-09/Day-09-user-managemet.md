## Day 09 – Linux User & Group Management Challenge


### Practice user and group management by completing the following tasks

 - Create Users and set passwords
 - Create Groups  assign users to Group
 - Configure shared directories
 - Manage permissions
 - Configure SSH login to custom users

### Task 1: Create Users

created following users

- `tokyo`
- `berlin`
- `professor`

<img width="402" height="144" alt="02-Users-home-directories" src="https://github.com/user-attachments/assets/cbe74447-44ea-4465-ab1e-cf4dcfa2d161" />


Command used :
- sudo useradd -m Tokyo
- sudo adduser berlin
- sudo useradd -m professor
- sudo passwd professor

Verification:

cat /etc/passwd

<img width="837" height="82" alt="01-Users" src="https://github.com/user-attachments/assets/5c5d32d6-ef19-40c3-b1ae-6c6f00fb5d92" />

### Task 2: Create Groups 

Create two groups:
- `developers`
- `admins`

Commands used:
- sudo groupadd developers
- sudo groupadd admins

Verification: cat /etc/group | grep -E "developers|admins"

<img width="820" height="396" alt="03-users-groups" src="https://github.com/user-attachments/assets/19250489-ac46-4538-a05b-0c1198ad6060" />

### Task 3: Assign to Groups 

Assign users:
|`tokyo` | `developers`|
| `berlin`| `developers` + `admins` (both groups)|
| `professor` | `admins`|

commands:
 - sudo gpasswd -a tokyo developers
 - sudo gpasswd -a berlin admins
 - sudo gpasswd -a berlin developers
 - sudo gpasswd -a professor admins
 
Verification:
 
cat /etc/group

<img width="547" height="163" alt="04-users-added-to-group" src="https://github.com/user-attachments/assets/3031fa8c-2e88-49b7-9f05-9abd8fc141e1" />


### Task 4: Shared Directory

1. Created directory: `/opt/dev-project`
2. Set group owner to `developers`
3. Set permissions to `775` (rwxrwxr-x)
4. Test by creating files as `tokyo` and `berlin`

<img width="813" height="689" alt="05-shared-directoy" src="https://github.com/user-attachments/assets/d57fa23f-d949-4475-9aa7-0a026a8abef2" />


commands :
- sudo mkdir -p /opt/dev-project
- sudo chgrp developers /opt/dev-project/
- sudo chmod 775 /opt/dev-project/
- cd /home -> su - tokyo -> touch test.txt -> ls -l 
- su - berlin -> touch test.txt -> ls -l 


### Task 5: Team Workspace 

1. Create user `nairobi` with home directory
2. Create group `project-team`
3. Add `nairobi` and `tokyo` to `project-team`
4. Create `/opt/team-workspace` directory
5. Set group to `project-team`, permissions to `775`
6. Test by creating file as `nairobi`

Commands:
- sudo useradd -m nairobi
- Sudo groupadd Project-team
- sudo gpasswd -a Nairobi Project-team
- sudo gpasswd -a tokyo Project-team
- sudo mkdir /opt/team-workspace
- sudo chgrp Project-team /opt/team-workspace
- sudo chmod 775 /opt/team-workspace/

<img width="528" height="189" alt="07-nairobi-group" src="https://github.com/user-attachments/assets/5c9514c0-2362-4aff-82e9-6e4cea9940d8" />


Users & Groups Created

| Users | Groups |
|---|---|
| Tokyo | developers |
| berlin | admins |
| professor | project-team |
| Nairobi  |    |

Listed who is in which groups

| Group | User |
|---|---|	
| Developers 	|	tokyo, berlin |
| admins	|	berlin, professor |
| project-team	|	nairobi, Tokyo |

Listed directories with permissions

| Directories |	Permissions |
|---|---|
| team-workspace |	drwxrwxr-x |
| dev-project 	 |	drwxrwxr-x |

Commands used

| Command |		Purpose |
|---|---|
| mkdir -p "directoy_name"	|	Create directory |
| touch "file_name		|	Create file |
| sudo useradd -m "username"	|	Create User |
| sudo passwd "username"	|	Set password |
| cat /etc/passwd		|	Verify added users |
| sudo groupadd "groupname"	|	Create group |
| sudo gpasswd -a "username" "groupname" |	 Add user to group |
| cat /ect/group 			|	 Verify added group |
| sudo chgrp "groupname" "directoy_name" |	 Change group ownership |
| sudo chmod "permission" "directoy_name" |	 set permissions |



