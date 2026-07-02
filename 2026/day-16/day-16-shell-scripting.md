# Day 16 – Shell Scripting Basics

### Task 1: Your First Script
1. Create a file `hello.sh`
- vim hello.sh

2. Add the shebang line `#!/bin/bash` at the top
- #!/bin/bash

3. Print `Hello, DevOps!` using `echo`
- echo "Hello, DevOps!"

4. Make it executable and run it
chmod +x hello.sh
./hello.sh

<img width="423" height="183" alt="Task_1" src="https://github.com/user-attachments/assets/5d6085b2-b2f7-4c6b-ba83-dc39b50aeacd" />

<img width="346" height="200" alt="removed_shebang" src="https://github.com/user-attachments/assets/32c16340-12e1-415c-88f0-6870925af32a" />

What happens if you remove the shebang line?
- The script runs after removing shebang line 
- The shell script picks the system's default shell (often sh/Dash), which may break Bash-specific features.
- `./hello.sh` - The kernel checks for a shebang to identify the interpreter. If no shebang is found, the script is executed using the current shell.
- `bash hello.sh` - The script is explicitly executed by the Bash shell, independent of the presence of a shebang.
- `sh hello.sh` - The script is executed using the `sh shell`,which may differ in behavior from bash

### Task 2: Variables
1. Create `variables.sh` with:
   - A variable for your `NAME`
   - A variable for your `ROLE` (e.g., "DevOps Engineer")
   - Print: `Hello, I am <NAME> and I am a <ROLE>`
<img width="573" height="196" alt="variables_single_double" src="https://github.com/user-attachments/assets/01b3955b-456c-476c-8fad-e3fae99fc876" />

<img width="471" height="368" alt="variable_sh" src="https://github.com/user-attachments/assets/f93d770e-a3e0-4efe-924e-0ddf3ef9ab42" />


2. Try using single quotes vs double quotes — what's the difference?
 * Using double quote `" "` - Allow **variable expansion**
 * Using single quote `' '` - Treat every character exactly as written

### Task 3: User Input with read
1. Create `greet.sh` that:
   - Asks the user for their name using `read`
   - Asks for their favourite tool
   - Prints: `Hello <name>, your favourite tool is <tool>`
     
<img width="565" height="193" alt="Task3" src="https://github.com/user-attachments/assets/31bfea21-e620-4a38-ba94-fe137d782a05" />


<img width="562" height="274" alt="greet_sh" src="https://github.com/user-attachments/assets/60f75401-c039-4964-b13d-111556a05078" />

### Task 4: If-Else Conditions
1. Create `check_number.sh` that:
   - Takes a number using `read`
   - Prints whether it is **positive**, **negative**, or **zero**

<img width="567" height="229" alt="if_else" src="https://github.com/user-attachments/assets/6106adeb-e0bf-4eb3-89b0-879044f0741f" />

<img width="482" height="272" alt="check_number_sh" src="https://github.com/user-attachments/assets/03dacdff-8bcf-4e35-92fb-bd9ee843d8e1" />

2. Create `file_check.sh` that:
   - Asks for a filename
   - Checks if the file **exists** using `-f`
   - Prints appropriate message
  
<img width="525" height="227" alt="file_check" src="https://github.com/user-attachments/assets/290dce1c-cfa7-4b7f-b704-332e34547e02" />

<img width="556" height="222" alt="file_check_sh" src="https://github.com/user-attachments/assets/ef8809b8-4071-40c8-a49c-304ddf119b9f" />

### Task 5: Combine It All
Create `server_check.sh` that:
1. Stores a service name in a variable (e.g., `nginx`, `sshd`)
2. Asks the user: "Do you want to check the status? (y/n)"
3. If `y` — runs `systemctl status <service>` and prints whether it's **active** or **not**
4. If `n` — prints "Skipped."

<img width="552" height="305" alt="service_chek" src="https://github.com/user-attachments/assets/348f53cb-3238-4eff-95f8-227075c064b4" />

<img width="560" height="318" alt="service_chek_sh" src="https://github.com/user-attachments/assets/c2aa748a-a2c8-4154-b222-10aeb4e710c1" />


## What I learned -


* How to write and execute Bash shell scripts using the shebang (`#!/bin/bash`), If `#!/bin/bash` is not added to the top of the shell script, the shell script picks the system's default shell (often sh/Dash), which may break Bash-specific features.
* How to define variables in shell script, When defining a variables there shouldn't be any spaces i.e. `NAME="Reshma"`. 
* How to read user input with `read -p`.
* How variable assignment works in Bash,including accessing variables with `$` and understanding single vs double quotes. Double quotes should be used instead of single quotes for echo command to run the variables within the message.
* How to control script flow using conditional statements (`if`, `elif`, `else`) and test operators (`-f`, `-gt`, `-lt`).While using `if` command, we should use `[]` brackets with proper spaces i.e. `if[ condition ]; then` and `if` command should end with `fi`.
* How to check file existence and numeric conditions inside shell scripts.
* How to use `systemctl is-active` to programmatically check whether a service is running instead of relying on verbose status output.
* We can automate shell commands inside the shell script,by make file executable using `chmod +x hello.sh` and running it with `./hello.sh`.

