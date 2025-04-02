# 🐚 Linux Command Line Cheatsheet — Otter Rescue Adventure Edition 🦦

---

## 📍 Basic Navigation & File Inspection

1. `~` — Home directory  
2. `pwd` — Print current working directory  
3. `ls` — List directory contents  
    - `-l` — Long format (e.g., `ls -l`)  
    - `-lt` — Long format, sorted by time (newest first)  
    - `-ltr` — Long format, sorted by time (oldest first)  
    - `-ltrh` — Long format, oldest first, human-readable sizes  
    - `-a` — Show all files including hidden ones  
    - `-1` - Show 1 file per line
4. `cd folder_name` — Change directory  
    - `cd ..` — Go to parent directory  
    - `cd .` — Stay in current directory  
5. `find` — find files
    - e.g., `find . -name "*fish*"`: find all the files whose name contains `fish`


---

## 📍 Viewing File Content

5. `cat file.txt` — Print entire content  
6. `head file.txt` — Print first 10 lines  
7. `tail file.txt` — Print last 10 lines  

---

## 📍 Editing Files

8. `nano file.txt` — Open file in Nano editor  
    - Ctrl+O to save, Ctrl+X to exit, Ctrl+K to delete a line  
9. `vi file.txt` — Open file in Vi editor  
    - Press `i` to insert  
    - Press `Esc`, then type `:wq` and hit `Enter` to save and quit  
    - Type `:q!` and hit `Enter` to quit without saving  

---

## 📍 Creating and Modifying Files

10. `touch file.txt` — Create an empty file or update timestamp if the file already exist
11. `echo "text" > file.txt` — Write text to file (overwrite)  
12. `echo "text" >> file.txt` — Append text to file  
13. `cat file1.txt file2.txt > file3.txt` — Combine files  

---

## 📍 File Movement, Copying, and Deletion

14. `mv oldname.txt newname.txt` — Rename a file  
15. `mv file.txt folder/` — Move file to folder  
16. `cp file.txt copy.txt` — Copy file  
17. `cp -r folder1 folder2` — Copy folder recursively  
18. `rm file.txt` — Delete a file  
19. `rm -r folder/` — Recursively delete folder  
20. `rm -f file.txt` — Force delete file (no warning)  
21. `rm -rf folder/` — Forcefully delete folder and contents  

---

## 📍 Directory Management

22. `mkdir new_folder` — Create a new folder  
23. `mkdir -p parent/child` — Create nested folders including parent folders if parent folders do not exist yet
24. `rmdir empty_folder` — Remove empty folder  

---

## 📍 Permissions & Ownership

25. `chmod 400 key.pem` — Change file permission  
    - first digit = privillage of owner of the file; second digit = other people in the same group; third digit = everyone else in the world
    - 4 = read, 2 = write, 1 = execute  
    - 7 = 4 + 2 + 1 = read & write & execute
    - Examples:  
        - `400` = read-only by owner  
        - `600` = read/write by owner  
        - `756` = full access for owner, read & execute for others in the same group, read & write for everyone else in the world
26. `chown user:group folder/` — Change ownership of the folder 
27. `sudo` — Run command with superuser privileges, "super user do" 

---

## 📍 Wildcards & Patterns

28. `*` — Wildcard: matches anything  
    - Example: `mv fish* folder/`  
29. `?` — Matches a single unknown character  

---

## 📍 Print and Search

30. `echo "text"` — Print text to terminal  
31. `grep pattern file.txt` — Search for pattern  
    - `-i` — Ignore case  
    - `-v` — Display lines with no match
    - `-n` — precede each matching line with line number 
    - `-c` — Print only total count of matched lines 

---

## 📍 System & File Info

32. `history` — Show command history  
33. `df -h` — Show disk space in human-readable format  
34. `clear` — Clear the screen  
35. `wc file.txt` — Count number of words in this file
    - `-l` — Count number of lines in this file
36. `sort file.txt` — Sort lines alphabetically  

---

## 📍 Compression

37. `zip file.zip file.txt` — Compress file  
38. `unzip file.zip` — Decompress file  

---

## 📍 Process Management

39. `Ctrl+C` — Stop running command  
40. `exit` — exit the SSH connection to a server, or exit a mode of being a user
41. `COMMAND FILE1 | COMMAND`  — Connect output of commands
    - for instance, `cat FILE1 | sort`
