| command | description                                                 |
| ------- | ----------------------------------------------------------- |
| `pwd`   | print working directory                                     |
| `ls`    | list all content inside directory                           |
| `ls -l` | aditional list all file -> larget list with its permissions |
```davi@davi:~/Documents/Linux/Linux$ ls -la
total 24
drwxrwxr-x 5 davi davi 4096 Jun 18 21:13  .
drwxrwxr-x 3 davi davi 4096 Jun 18 14:29  ..
drwxrwxr-x 2 davi davi 4096 Jun 18 21:13  Fundamentals
drwxrwxr-x 2 davi davi 4096 Jun 18 21:13  Images
-rw-rw-r-- 1 davi davi   86 Jun 18 21:13 'Linux Fundamentals.md'
drwxrwxr-x 5 davi davi 4096 Jun 18 14:45  .obsidian
```

`drwxrwxr-x` means type and permissions
1. `d` / `-` : directory or file
2. `rwx` : read write execute -> for owner, group, and other
`drwxrw-r--` -> means owner can read, write, and execute, anything in that user group can read and write, and others can only read

`touch` : create file
`mkdir` : create directory
`mkdir -p A/B/C...` : will create folder A, with B, with C
`tree` : display folder structure until subfolders
```
.
├── A
│   └── B
│       └── C

```
`rm -rf` : delete directory recursively
`mv <file1> <file2>` : rename file
`mv <file1> <directory>` : move file from current directory to desired directory
`cp <file1> <directory>` : copy file into desired directory

`nano <file1>` : use GNU nano to edit desired file
`Ctrl + O` then enter -> `Ctrl + X` to save that file

`which <package>` : check if package is available
`find <args>` : command to search file list based on our arguments

| Args                | Description                                                 |
| ------------------- | ----------------------------------------------------------- |
| -type f             | Filetype (f: file)                                          |
| -name "*.conf"      | Indicate search by filename, and extension is .conf         |
| -user root          | Owner is root                                               |
| -size +20k          | Size is Larger than 20KiB                                   |
| -newermt 2020-03-03 | Set the date newer than that date                           |
| 2>/dev/null         | suppress permission errors for directories you can’t access |
```
find / -type f -name "*.conf" -size -28k -size +25k -newermt 2020-03-03 2>/dev/null
```