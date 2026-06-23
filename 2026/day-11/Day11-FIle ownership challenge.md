# Day 11 – File Ownership Challenge (chown & chgrp)

---

### Task 1: Understanding Ownership 

1. Run `ls -l` in your home directory
2. Identify the **owner** and **group** columns
3. Check who owns your files

**Format:** `-rw-r--r-- 1 owner group size date filename`

### Meaning of Each Part

<img width="579" height="186" alt="task1" src="https://github.com/user-attachments/assets/9159592b-a65e-4122-87ef-4653ce848439" />

| Part | Value | Meaning |
|----|----|----|
| Permissions | `-rw-r--r--` | Who can read/write the file |
| Owner | `vinod` | User who owns the file |
| Group | `vinod` | Group that owns the file |
| Size | `12` | File size in bytes |
| Date | `Jun 23 00:25` | Last modified date & time |
| Filename | `day-11.txt` | Name of the file |

### Who Owns the File?

- **Owner:** `vinod`
- **Group:** `vinod`

### This Means:

- **vinod** is the **owner** of the file
- The file belongs to the **group** named **vinod**

### Difference Between Owner and Group

- **Owner** → The main user who created or owns the file
- **Group** → A set of users who may share access to the file


### Task 2: Basic chown Operations 

1. Create file `devops-file.txt`
2. Check current owner: `ls -l devops-file.txt`
3. Change owner to `tokyo` 
4. Change owner to `berlin`
5. Verify the changes

<img width="702" height="410" alt="task2" src="https://github.com/user-attachments/assets/5e9dc1ed-2e9b-494c-90d6-9002cbe397a9" />

### Task 3: Basic chgrp Operations (15 minutes)

1. Create file `team-notes.txt`
2. Check current group: `ls -l team-notes.txt`
3. Create group: `sudo groupadd heist-team`
4. Change file group to `heist-team`
5. Verify the change

<img width="808" height="436" alt="task3" src="https://github.com/user-attachments/assets/5716994d-539a-4631-8886-530686b6704e" />


### Task 4: Combined Owner & Group Change 

Using `chown` you can change both owner and group together:

1. Create file `project-config.yaml`
2. Change owner to `professor` AND group to `heist-team` (one command)
3. Create directory `app-logs/`
4. Change its owner to `berlin` and group to `heist-team`

<img width="824" height="423" alt="task4" src="https://github.com/user-attachments/assets/b527043c-39e8-43df-b9de-eaa01334652f" />

### Task 5: Recursive Ownership (20 minutes)

1. Create directory structure:
   ```
   mkdir -p heist-project/vault
   mkdir -p heist-project/plans
   touch heist-project/vault/gold.txt
   touch heist-project/plans/strategy.conf
   ```

<img width="742" height="163" alt="task5 1" src="https://github.com/user-attachments/assets/50540e98-2d1f-4417-9197-a387936459ac" />


2. Create group `planners`: `sudo groupadd planners`

<img width="580" height="113" alt="task5 2" src="https://github.com/user-attachments/assets/38f6d11f-44dc-457a-8a39-ae65cd0c1bb9" />


3. Change ownership of entire `heist-project/` directory:
   - Owner: `professor`
   - Group: `planners`
   - Use recursive flag (`-R`)

<img width="816" height="272" alt="task5 3" src="https://github.com/user-attachments/assets/20c61738-a7d7-4bb7-8ada-a0bec1f04100" />


4. Verify all files and subdirectories changed: `ls -lR heist-project/`

<img width="963" height="462" alt="task5 4" src="https://github.com/user-attachments/assets/443eab32-bcad-4a5a-9917-17f253e7d2b4" />







