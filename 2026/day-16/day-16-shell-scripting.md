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


