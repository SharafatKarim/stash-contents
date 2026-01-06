## Windows Basic Commands

1. `dir`: Lists files and directories in the current directory.  
2. `cd`: Changes the current directory.  
3. `md`: Creates a new directory.  
4. `rd`: Removes (deletes) a directory.  
5. `copy`: Copy files.  
6. `move`: Move files.
7. `del`: Delete files.  
8. `ren`: Rename files.  
9. `type`: Displays the content of a text file.  
10. `tree`: Generates directory structure.
11. `edit`: Opens a simple text editor.  (or, use `notepad`)
12. `chkdsk`: Checks a disk for errors.  
13. `systeminfo`: Shows Your PC's Details
14. `powercfg /batteryreport`: Battery report generation.
15. `tree`: Displays a graphical representation of the directory structure.  
16. `ping`: Sends ICMP Echo Request packets to test network connectivity.  
17. `ipconfig`: Displays IP configuration information.  
18. `date`: Displays or sets the system date.  
19. `time`: Displays or sets the system time.  
20. `set`: Displays, sets, or removes environment variables.  
21. `tasklist`: Displays a list of currently running tasks.  
22. `taskkill`: Terminates one or more running tasks.  
23. `fc`: Compares two files or sets of files.  
24. `help`: Displays help information for commands.  
25. `exit`: Exits the Command Prompt.

## Running Programs in Windows

#### Running C/C++ codes (windows)
```
g++ input.cpp
.\a.exe
```

#### Running assembly codes (windows)
Download and install `nasm` compiler,
```shell
winget install nasm
```

Write a simple `.asm` code,
```shell
; hello.asm (Windows x64, NASM)

default rel
extern printf
global main

section .data
    msg db "Hello, World!", 10, 0

section .text
main:
    sub rsp, 40        ; shadow space + stack alignment
    lea rcx, [msg]    ; first argument (Windows x64)
    call printf
    add rsp, 40

    xor eax, eax
    ret
```
Compile and run the code,
```shell
nasm -f win64 hello.asm -o hello.obj	
gcc hello.obj -o hello.exe
.\hello.exe
```

#### Running python/... codes
Directly run the relevant command,
```
python source.txt
```

## Running Programs in Android
Search for `termux fdroid` and install it,
- [Termux - FDroid Store](https://f-droid.org/en/packages/com.termux/)

Install the required packages, like,
```shell
pkg install clang
```

Use a CLI based text editor for editing files,
```shell
nano input.cpp
```

Finally compile and run,
```shell
g++ input.cpp
.\a.out
```