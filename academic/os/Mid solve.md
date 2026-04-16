# Operating Systems Sessional: Mid-Term Examination Archive

This document contains a compilation of Mid-Term Examination questions for the course **CIT 322: Operating Systems Sessional**, spanning sessions from 2017 to 2023.

## Mid Term Examination: July–December 2023

**Course Code:** CIT 322 | **Course Title:** Operating Systems Sessional
**Session:** 2020-21 | **Program:** B.Sc. Engg.(CSE) | **Semester:** 6th
**Total Marks:** 15 | **Instructions:** Answer the marked questions.

### SET-A (Answer any one from 1 to 3)

1. ~~Implement Peterson's solution for ensuring synchronization. **[07]**~~
    
2. ~~Implement mutex locks to ensure synchronization.~~
    
3. ~~Semaphore implementation to solve busy waiting problem.~~
    

### SET-B (Answer one from 4–5; Question 6 is mandatory)

**[✓] 4. Multithreading Basics [04]**

Write a code to demonstrate how to create and start Python's or Java's threads using the threading module (or `Thread` class).

- It should run a function `print_name` that prints a name along with provided arguments.
    
- This example should create two threads, start them using the `start()` method, and wait for completion using the `join()` method.
    

**5. Concurrent Calculation [04]**

Write code to use Python's or Java's threading module to calculate the square and cube of a number concurrently.

- Create two threads (`t1` and `t2`) for these calculations.
    
- Print results in parallel and print "Done!" only when both threads finish.
    
- _Note: Threading is used to achieve parallelism and improve performance for computationally intensive tasks._
    

**6. Linux Command Operations [04]**

Perform/Explain the following terminal operations:

1. Display information about files in the current directory. 
   ```bash
   ls
   ls -lah
   ```
    
2. Create a directory with your own student name; inside it, create a file. Then create a directory in the home directory and copy the previously created file there.
   ```bash
   mkdir sharafat
   touch text.txt
   cp /home/sharafat/sharafat/test.txt /home/sharafat/test
   cp test.txt ~/test
   ```
    
3. Navigate between different folders.
   ```bash
   cd
   ```
    
4. Remove empty directories from the directory list.
   ```bash
   find . -type d -delete
   ```
    
5. File copy/cut and paste operations via terminal.
   ```bash
   cp source/ destination/
   mv source/ destination/
   ```
    
6. Download files from the internet.
   ```bash
   wget URL
   aria2c URL
   ```
    
7. Display the current user's name.
   ```bash
   whoami
   echo $USER
   ```
    
8. View the calendar in the terminal.
   ```bash
   cal
   cal 8 11 2002
   ```
    
9. Check the details of the file system.
   ```bash
   neofetch
   fastfetch
   lscpu
   lsblk
   ```
    
10. Check lines, word count, and characters in a file using different options.
    ```bash
    wc filename
    wc -l filename
    wc -c filename
    wc --help
    ```
    

## Mid Term Examination: July–December 2022 (PART-B)

**Course Code:** CIT 322 | **Course Title:** Operating Systems Sessional

**Session:** 2019-20 | **Program:** B.Sc. Engg.(CSE) | **Semester:** 6th

**Total Marks:** 08

1. **Compiling Environment:** Running a C/C++ Program in Linux. **[02]**
   ```bash
   g++ input.cpp
	.\a.exe
   ```
    
2. **Linux Shell Commands:** Use commands to perform the following: **[06]**
    
    - (i) Show home directory of your user.
      ```bash
      echo $HOME
      ```
        
    - (ii) List files in the current directory.
      ```bash
      ls
      ```
        
    - (iii) Change directory.
      ```bash
      cd
      ```
        
    - (iv) Create a folder/directory.
      ```bash
      mkdir name
      ```
        
    - (v) Delete files and directories.
      ```bash
      rm filename
      ```
        
    - (vi) Create a file.
      ```bash
      touch file.txt
      ```
        
    - (vii) Access manual pages (help) for a command.
      ```bash
      ls --help
      man ls
      ```
        
    - (viii) Change file permissions (make a file executable).
      ```bash
      chmod +x filename
      ```
        
    - (ix) Move files via command line.
      ```bash
      mv source destination
      ```
        
    - (x) Locate a file in the system.
      ```bash
      ls -R | grep input.jpg
      ```
        
    - (xi) Check server connectivity (ping).
      ```bash
      ping 9.9.9.9
      ping -c 5 sharafat.xyz
      ```
        
    - (xii) Redirect data/text into a file.
      ```bash
      ping -c 5 sharafat.xyz > file.txt
      ```
        

## Mid Term Examination: July–December 2021

**Course Code:** CIT 322 | **Course Title:** Operating Systems Sessional

**Session:** 2018-19 | **Program:** B.Sc. Engg.(CSE) | **Semester:** 6th

**Total Marks:** 15 | **Instructions:** Answer questions 1, 2, 3 and marked questions.

1. Installation of Linux with Virtual Machine. **[01]**
    
2. Running a C/C++ Program in Linux. **[02]**
    
3. Running a Java Code in Linux. **[02]**
    
    **[✓] 4. System Administration & Navigation Commands: [10]**
    
    - List home directory, navigate folders, and create/delete files/directories.
        
    - Check disk space in partitions.
        
    - Run commands with administrative/root privileges (`sudo`).
      ```bash
      sudo commmand
      ```
        
    - Compress files into a `.zip` archive.
      ```bash
      zip compressed.zip file_1 file_2 ...
      ```
        
    - Check disk usage of a specific file.
        
    - Check network connection.
        

## Mid Term Examination: July–December 2020

**Course Code:** CIT 322 | **Course Title:** Operating Systems Sessional

**Session:** 2017-18 | **Program:** B.Sc. Engg.(CSE) | **Semester:** 6th

**Total Marks:** 15 | **Instructions:** Answer the marked questions.

### 1. FCFS Scheduling Analysis [10]

Consider three CPU-bound processes arriving at an FCFS scheduler:

|   |   |   |
|---|---|---|
|**Process**|**Arrival Time**|**Duration (Burst)**|
|$P_1$|0|3|
|$P_2$|1|12|
|$P_3$|5|1|

- **Tasks:** Give the schedule (Gantt Chart) and compute the average waiting time.
    
- **Analysis:** Define the "Convoy Effect." Provide an alternative arrival order that improves average waiting time and a second order that demonstrates the convoy effect.
    

### 2. Comparative Scheduling [10]

Compare the average waiting time for FCFS, SJF, and SRTF for the following processes:

|   |   |   |
|---|---|---|
|**Process**|**Arrival Time**|**Burst Time**|
|$P_1$|0|8|
|$P_2$|3|3|
|$P_3$|5|4|
|$P_4$|6|6|

### 3. Algorithm Simulation

**[✓] 3. Simulate the CPU scheduling algorithm Round-Robin.** **[10]**

4. Simulate the Priority Scheduling algorithm (Random). **[10]**

5. Simulate the First Come First Serve (FCFS) algorithm. **[10]**

6. Simulate the Shortest Job First (SJF) (Non-Preemptive) algorithm. **[10]**

7. Simulate the Shortest Job First (SJF) algorithm. **[10]**

8. Simulate the Shortest Remaining Time (SRT) algorithm. **[10]**

### 9. Linux Customization & Management [05]

**[✓] Tasks:**

1. Change wallpaper and screensaver via Linux command line.
    
2. Create a directory (student name), create a file within, and copy it to a new directory in the home folder.
    
3. Create disk partitions.
    
4. Install and configure a printer.
    
5. Perform file copy, cut, and paste operations.