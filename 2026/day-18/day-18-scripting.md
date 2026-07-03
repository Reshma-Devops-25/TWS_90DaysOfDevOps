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



