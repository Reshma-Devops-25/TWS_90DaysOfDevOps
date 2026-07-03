# Day 17 – Shell Scripting: Loops, Arguments & Error Handling


### Task 1: For Loop
1. Create `for_loop.sh` that:
   - Loops through a list of 5 fruits and prints each one

<img width="469" height="157" alt="for_loop_sh" src="https://github.com/user-attachments/assets/93aa31d1-3efc-4cac-a18f-b8bc8b6ec02a" />

<img width="554" height="154" alt="for_loop" src="https://github.com/user-attachments/assets/ed54abe6-210c-4c2b-9905-a6561536fba6" />
  
     
2. Create `count.sh` that:
   - Prints numbers 1 to 10 using a for loop

<img width="292" height="152" alt="count_sh" src="https://github.com/user-attachments/assets/b7e14a61-89b8-440d-ae52-a7a10d54f202" />


<img width="606" height="248" alt="count" src="https://github.com/user-attachments/assets/841dccde-db8a-40cc-9c28-c1f1820359f1" />

### Task 2: While Loop
1. Create `countdown.sh` that:
   - Takes a number from the user
   - Counts down to 0 using a while loop
   - Prints "Done!" at the end

<img width="521" height="237" alt="countdown_sh" src="https://github.com/user-attachments/assets/2d0a0a2f-171e-4295-9919-d80eed20886d" />


<img width="519" height="222" alt="countdown" src="https://github.com/user-attachments/assets/1d2f10a1-f63e-4b4b-806d-86a6a64a0f36" />

### Task 3: Command-Line Arguments
1. Create `greet.sh` that:
   - Accepts a name as `$1`
   - Prints `Hello, <name>!`
   - If no argument is passed, prints "Usage: ./greet.sh <name>"
<img width="385" height="202" alt="greet1_sh" src="https://github.com/user-attachments/assets/558392d5-4408-403e-a787-726ee9377a3d" />

<img width="619" height="208" alt="greet1" src="https://github.com/user-attachments/assets/32bd81b8-8579-415f-aaa7-c1125f9bc96d" />


2. Create `args_demo.sh` that:
   - Prints total number of arguments (`$#`)
   - Prints all arguments (`$@`)
   - Prints the script name (`$0`)

<img width="428" height="230" alt="arguments_sh" src="https://github.com/user-attachments/assets/df9eab2c-3eec-4bad-9013-1004baf06972" />


<img width="790" height="331" alt="arguments" src="https://github.com/user-attachments/assets/37ff8f7c-284c-46cf-8811-1fc97198f138" />

### Task 4: Install Packages via Script
1. Create `install_packages.sh` that:
   - Defines a list of packages: `nginx`, `curl`, `wget`
   - Loops through the list
   - Checks if each package is installed (use `dpkg -s` or `rpm -q`)
   - Installs it if missing, skips if already present
   - Prints status for each package


<img width="696" height="427" alt="install_pakage_sh" src="https://github.com/user-attachments/assets/2677e9c1-59d8-416b-b426-c87c045de9e3" />


<img width="560" height="148" alt="install_pakage" src="https://github.com/user-attachments/assets/6c157d8a-4ea8-4c89-9cfa-c24d554a6592" />

### Task 5: Error Handling
1. Create `safe_script.sh` that:
   - Uses `set -e` at the top (exit on error)
   - Tries to create a directory `/tmp/devops-test`
   - Tries to navigate into it
   - Creates a file inside
   - Uses `||` operator to print an error if any step fails

<img width="532" height="250" alt="safe_script_sh" src="https://github.com/user-attachments/assets/3b1461be-2a2b-4460-b9cd-56c197ed4761" />



<img width="1105" height="357" alt="safe_script" src="https://github.com/user-attachments/assets/6d9b5017-9fbc-4f1a-9625-69903b7c9687" />


2. Modify your `install_packages.sh` to check if the script is being run as root — exit with a message if not.

<img width="669" height="588" alt="modified_install_package_sh" src="https://github.com/user-attachments/assets/ab59125c-39e6-455d-a593-1e6bb7779d6c" />


<img width="706" height="362" alt="modified_install_package" src="https://github.com/user-attachments/assets/47dd6901-a21d-40ba-8d77-a08b9329b198" />





















