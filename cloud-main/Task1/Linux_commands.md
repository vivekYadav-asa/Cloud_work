# Linux Commands Used

This file contains the Linux commands used while completing the **Linux Search Project** assignment on Kali Linux.

---

## Navigation

### Show current directory

```bash
pwd
```

Displays the current working directory.

---

### List files and folders

```bash
ls
```

List all files.

```bash
ls -l
```

Detailed list.

```bash
ls -la
```

Detailed list including hidden files.

---

### Change directory

```bash
cd FolderName
```

Move into a folder.

```bash
cd ..
```

Move to the parent directory.

```bash
cd ~
```

Go to the home directory.

---

## Directory Operations

### Create a directory

```bash
mkdir Linux_Search_Project
```

Create one folder.

```bash
mkdir HR IT Sales Finance
```

Create multiple folders at once.

---

### View directory structure

```bash
find .
```

Display the complete folder hierarchy.

---

## File Operations

### Create files

```bash
touch file1.txt
```

Create an empty file.

```bash
touch file1 file2 file3
```

Create multiple files.

---

### Delete files

```bash
rm filename
```

Delete a file.

---

### Delete directories

```bash
rm -r FolderName
```

Delete a directory recursively.

---

## Writing Data

### Overwrite a file

```bash
echo "Linux is powerful." > file.txt
```

Replace all existing content.

---

### Append to a file

```bash
echo "Docker is widely used." >> file.txt
```

Add content at the end of the file.

---

## Editing Files

### Open Nano editor

```bash
nano file.txt
```

Edit a file.

Useful Nano shortcuts:

```
Ctrl + O    Save
Enter       Confirm filename
Ctrl + X    Exit
Ctrl + K    Cut current line
Ctrl + U    Paste line
Ctrl + W    Search
Ctrl + \
Replace
```

---

## Viewing File Content

### Display complete file

```bash
cat file.txt
```

---

### Display first lines

```bash
head file.txt
```

First 10 lines.

```bash
head -2 file.txt
```

First 2 lines.

---

### Display last lines

```bash
tail file.txt
```

Last 10 lines.

```bash
tail -2 file.txt
```

Last 2 lines.

---

## Searching

### Find all text files

```bash
find . -name "*.txt"
```

---

### Search for a word

```bash
grep "Linux" *.txt
```

---

### Search recursively

```bash
grep -r "Linux" .
```

---

### Show only filenames

```bash
grep -rl "Linux" .
```

---

### Count occurrences

```bash
grep -roh "Linux" . | wc -l
```

---

## Counting

### Count files

```bash
find . -type f | wc -l
```

---

### Count directories

```bash
find . -type d | wc -l
```

---

### Count lines in each file

```bash
wc -l */*
```

---

## Duplicate Words

```bash
cat */* | tr ' ' '\n' | sort | uniq -d
```

Find duplicate words.

---

## Unique Words

```bash
cat */* | tr ' ' '\n' | sort | uniq
```

Display unique words.

---

## Command History

```bash
history
```

Show previously executed commands.

---

### Search command history

```bash
history | grep nano
```

---

## Terminal

### Clear terminal

```bash
clear
```

or

```
Ctrl + L
```

---

### Exit terminal

```bash
exit
```

or

```
Ctrl + D
```

---

## Shutdown

```bash
sudo poweroff
```

Safely shut down Kali Linux.

---

## Git Commands Used

### Check repository status

```bash
git status
```

---

### Stage changes

```bash
git add .
```

---

### Commit changes

```bash
git commit -m "Commit message"
```

---

### Push to GitHub

```bash
git push
```

---

## Summary

Commands covered in this project:

- `pwd`
- `ls`
- `cd`
- `mkdir`
- `find`
- `touch`
- `rm`
- `echo`
- `cat`
- `nano`
- `grep`
- `head`
- `tail`
- `wc`
- `sort`
- `uniq`
- `tr`
- `history`
- `clear`
- `exit`
- `git status`
- `git add`
- `git commit`
- `git push`
