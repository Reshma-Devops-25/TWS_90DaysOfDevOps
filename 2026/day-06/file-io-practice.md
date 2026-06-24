### Creating a file

- ubuntu@ip-172-31-21-180:\~$ touch notes.txt

### Writing text to a file

- ubuntu@ip-172-31-21-180:\~$ echo "Line 1" > notes.txt

### Appending new lines

- ubuntu@ip-172-31-21-180:\~$ echo "Line 2" >> notes.txt

- ubuntu@ip-172-31-21-180:\~$ echo "Line 3" >> notes.txt

- ubuntu@ip-172-31-21-180:\~$ echo "line 4" | tee -a notes.txt

line 4

### Reading the file back

- ubuntu@ip-172-31-21-180:\~$ cat notes.txt

Line 1

Line 2

Line 3

line 4


- ubuntu@ip-172-31-21-180:\~$ head -n 2 notes.txt

Line 1

Line 2

- ubuntu@ip-172-31-21-180:\~$ tail -n 2 notes.txt

Line 3

line 4
