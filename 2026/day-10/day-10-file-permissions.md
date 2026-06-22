# Day 10 – File Permissions & File Operations Challenge

## Challenge Tasks

### Task 1: Create Files 

1. Created an empty file `devops.txt` using `touch`
2. Created an `notes.txt` with some content using echo > Day-10 practice on File permissions and File Operations challenge > notes.txt 
3. Created an `script.sh` using vim script.sh with content: echo "Hello DevOps Lerner "

<img width="959" height="488" alt="Task_1" src="https://github.com/user-attachments/assets/8890e7c4-c1a1-4359-9122-671756661563" />


Verification : used command `ls -l` to see permissions

For all files read only permission in commaon

| File Permission |
|---|
| -rw-r--r-- |


### Task 2: Read Files 

1. Read `notes.txt` using `cat`
2. View `script.sh` in vim read-only mode using vim -R script.sh
3. Used command head -n 5 /etc/passwd to display top 5 lines from /etc/passwd 
4. Used command tail -n 5 /etc/passwd to display bottom 5 lines from /etc/passwd 

<img width="956" height="541" alt="Task_2" src="https://github.com/user-attachments/assets/4cd7e8d3-9f91-4e2c-91a9-3a6c2a95a600" />

---

### Task 3: Understand Permissions

For all files have read permission in common

| File Permission |
|---|
| -rw-r--r-- |

| Owner | Group | Others |
|---|---|
| read	| write |   -	|
| read  |   -   |   -   |
| raed  |   -   |   -   |
---

### Task 4: Modify Permissions

1. Made `script.sh` executable → using command sudo chmod 744 script.sh -> ./script.sh
2. Set `devops.txt` to read-only -> command used -> sudo chmod 444 devops.txt
3. set 640 permission to notes.txt -> sudo chmod 640 notes.txt
4. Created directory `project/' -> set permissions `755`

<img width="962" height="938" alt="Task_4" src="https://github.com/user-attachments/assets/d4f92e6f-55b9-4cc1-880a-2c7c4a4cdcb1" />

Verification: used `ls -l` after each change

---

### Task 5: Test Permissions

1. Tried to write to a read-only file - permission denied
2. Tried to execute a file without execute permission - Permission denied
3. -bash permission denied error message.
   
<img width="957" height="416" alt="image" src="https://github.com/user-attachments/assets/e6867ea6-4066-4b80-887e-aa6a07148c61" />

## Files Created
['devops.txt', 'notes.txt', 'script.sh']

## Permission Changes
| File Name | Permission chnage before | Permission change After |
|---|---|
| devops.txt | -rw-r--r-- | -r--r--r--|
| notes.txt  | -rw-r--r-- | -rw-r--r--|
| devops.txt | -rw-r--r-- | -rw-r--r--|

## Commands Used
- Create file : 'touch', 'vim', 'echo'
- Read file : 'cat', 'head -n', 'tail -n', 'vim -R'
- Permissions : 'chmod 444', 'chmod 640', 'chmod 755'

## What I Learned

1. **File Creation and Inspection:** I learned how to create and edit files using `touch`, `echo`, and `vim`.I also discovered how to open files safely in read-only mode using `vim -R` .Additionally, I used the `head` and `tail` commands to filter specific lines from system files (`like /etc/passwd`) to verify user accounts on the system.

2. **Managing Permissions with chmod:** I learned how to modify file and directory permissions using the chmod command. I practiced using both symbolic mode (e.g., chmod +x to make a script executable) and numeric mode (e.g., `chmod 755` for directories, chmod `444` for read-only files).

3. **Troubleshooting Access Control:** I observed how Linux permissions directly affect file operations. I saw "Permission denied" errors when trying to execute a script without the executable permission or write to a read-only file, and fixed them by adjusting permissions.



