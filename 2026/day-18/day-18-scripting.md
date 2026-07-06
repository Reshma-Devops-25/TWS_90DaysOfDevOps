# Day 18 – Shell Scripting: Functions & intermediate Concepts

### Task 1: Basic Functions
1. Create `functions.sh` with:
   - A function `greet` that takes a name as argument and prints `Hello, <name>!`
   - A function `add` that takes two numbers and prints their sum
   - Call both functions from the script
  
<img width="484" height="471" alt="function_sh" src="https://github.com/user-attachments/assets/f857d2ea-23dd-4da1-af10-cc5e45331b3a" />

<img width="602" height="340" alt="functions" src="https://github.com/user-attachments/assets/24a64f25-5710-4404-a2c3-9045d70c4a64" />

### Task 2: Functions with Return Values
1. Create `disk_check.sh` with:
   - A function `check_disk` that checks disk usage of `/` using `df -h`
   - A function `check_memory` that checks free memory using `free -h`
   - A main section that calls both and prints the results


<img width="412" height="401" alt="check_memory_sh" src="https://github.com/user-attachments/assets/021350a9-9b3f-4231-a35a-9f30df06569b" />

<img width="750" height="166" alt="check_memory" src="https://github.com/user-attachments/assets/bab7b728-c45c-431e-ad16-50fc59f5b497" />


### Task 3: Strict Mode — `set -euo pipefail`
1. Create `strict_demo.sh` with `set -euo pipefail` at the top
2. Try using an **undefined variable** — what happens with `set -u`?
3. Try a command that **fails** — what happens with `set -e`?
4. Try a **piped command** where one part fails — what happens with `set -o pipefail`?


<img width="567" height="453" alt="strict_demo" src="https://github.com/user-attachments/assets/9d5d3371-01c3-4c77-999f-f151eeb55bb8" />

<img width="554" height="437" alt="strict_demo_sh" src="https://github.com/user-attachments/assets/e0dc3eb9-d851-4c1f-947d-20b06247d2bb" />

What does each flag do?
- `set -e` → t terminates the execution when the error occurs
- `set -u` → It terminates the script if it found undefined(unset) variable is used.
- `set -o pipefail` → Pipeline fails if any command fails

### Task 4: Local Variables
1. Create `local_demo.sh` with:
   - A function that uses `local` keyword for variables
   - Show that `local` variables don't leak outside the function
   - Compare with a function that uses regular variables

<img width="620" height="375" alt="local_demo" src="https://github.com/user-attachments/assets/032057b6-9952-4152-a311-e806bf7a6817" />


<img width="890" height="548" alt="local_demo_sh" src="https://github.com/user-attachments/assets/4f45c175-cfe6-44c7-9a9d-63d0e4dc5af2" />

### Task 5: Build a Script — System Info Reporter
Create `system_info.sh` that uses functions for everything:
1. A function to print **hostname and OS info**
2. A function to print **uptime**
3. A function to print **disk usage** (top 5 by size)
4. A function to print **memory usage**
5. A function to print **top 5 CPU-consuming processes**
6. A `main` function that calls all of the above with section headers
7. Use `set -euo pipefail` at the top


<img width="1302" height="932" alt="system_info" src="https://github.com/user-attachments/assets/38ad0d14-624d-4e3e-9cea-291d4e1885ff" />


<img width="1079" height="963" alt="system_info_sh" src="https://github.com/user-attachments/assets/591e3f1e-fc04-4b28-9666-6ec02744d94a" />


## What I Learned

**Functions & Modularity** – Learned to create reusable, organized code blocks.This makes scripts cleaner, easier to read, and simpler to maintain.

**System Monitoring Scripts** – Explored fetching system info like memory,disk usage,and CPU processes.Useful for building quick automation for system health checks.

**Error Handling & Safety** – Using `set -euo pipefail` to catch undefined variables,failing commands,and pipeline errors early,making scripts more reliable.

**Variable Scope** – Understood the difference between local and global variables. Local variables stay inside functions, while global variables affect the wider script.

**Practical Automation** – Using a main function to orchestrate tasks helps make scripts modular,maintainable,and automation-friendly.

**Function Naming Pitfall** – Faced an issue where naming a function the same as a system command (uptime) caused an infinite loop.
Learned to avoid using system command names for functions.


