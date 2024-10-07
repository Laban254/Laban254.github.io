---
layout: post
title: "Mastering Command Line: I/O Redirection, Filters, and Shell Expansion 💻"
date: 2024-04-06 10:00:00 +0000
categories: 
  - blog
subtitle: "Essential concepts for effective command line usage in Linux."
background: '/img/posts/command-line.jpg'
tags: 
  - Linux
  - Command Line
  - Shell
  - I/O Redirection
  - Filters
  - Shell Expansion
---

## **INTRODUCTION**

There are many reasons why you should learn about I/O redirection, shell filters, and shell expansion. These concepts are essential for anyone who wants to use the command line effectively. Without an understanding of how these features work, it will be difficult to fully utilize the potential of the command line. Additionally, learning about these topics will give you a better understanding of how Linux works under the hood. Finally, being knowledgeable about I/O redirection, shell filters, and shell expansion will make it easier for you to troubleshoot any issues that might arise when using the command line.

## **I/O Redirections**

Redirection is a feature in Linux that allows you to change the standard input/output devices when executing a command. The basic workflow of any Linux command is that it takes input and produces output.

Each command performs all terminal-related activities with three files that the shell makes available to every command:

1.  **Standard input (stdin)**: Represented by **<**, it is the information inputted into the terminal through the keyboard or input device.
2.  **Standard output (stdout)**: Represented by **>**, it is the information outputted after a process is run.
3.  **Standard error (stderr)**: It is an error message outputted by a failed process.

### **Output Redirection**

The **`>`** symbol is used for output redirection.

```bash
    root@537302f1e700:~/fruits# ls -l > listings 
    root@537302f1e700:~/fruits# cat listings 
    total 0                                                    
    -rw-r--r-- 1 root root 0 Sep  7 13:46 apple                
    -rw-r--r-- 1 root root 0 Sep  7 13:46 Apple                
    -rw-r--r-- 1 root root 0 Sep  7 13:49 banana               
    -rw-r--r-- 1 root root 0 Sep  7 13:48 Banana               
    -rw-r--r-- 1 root root 0 Sep  7 13:47 cherry
```
The output of **ls** when redirected will be stored in the `listings` file. This is how you can redirect a command.

When you use the **">"** operator to redirect to a file with the same name, the information in the file is overwritten.

```bash
    root@537302f1e700:~/fruits# echo " welcome " > listings 
    root@537302f1e700:~/fruits# cat listings 
     welcome 
```
In this example, `echo "welcome" > listings` has overwritten the existing file.

To prevent overwriting a file, you can append to it using the output append operator **>>**.


```bash
    root@537302f1e700:~/fruits# echo " welcome " > listings 
    root@537302f1e700:~/fruits# cat listings 
     welcome                                                     
    root@537302f1e700:~/fruits# echo "welcome again" >> listings 
    root@537302f1e700:~/fruits# cat listings 
     welcome                                                     
    welcome again
```
### **Input Redirection**

The **"<"** symbol is used for stdin redirection.

For example:

```bash
    $ wc -l users
    2 users
    $


    $ wc -l < users
    2
    $
```
Note that there is a difference in the output produced by the two forms of the `wc` command. In the first case, the name of the file `users` is listed with the line count; in the second case, it is not.

In the first case, `wc` knows that it is reading its input from the file `users`. In the second case, it only knows that it is reading its input from standard input, so it does not display the filename.

## **Filters in Linux**

Filters are programs that take in plain text as standard input, transform it into a meaningful format, and then return it as standard output. These include:

### **1. `cat`**

The `cat` command displays the text of the file line by line.

```bash

    cat [path]
    
    root@537302f1e700:~/fruits# cat list 
    apple                                                      
    mango                                                      
    banana                                                     
    oranges
```
### **2. `head`**

The `head` command displays the first `n` lines of a file. If the number of lines is not specified, it prints the first 10 lines by default.


```bash
    head [lines-to-print] [path]
    
    root@537302f1e700:~/fruits# head list 
    apple                                                      
    mango                                                      
    banana                                                     
    oranges                                                    
    Melon                                                      
    mandarin                                                   
    Avocado                                                    
    coconut                                                    
    Cherry                                                     
    lime                                                       
    root@537302f1e700:~/fruits# head -3 list 
    apple                                                      
    mango                                                      
    banana                                                     
    root@537302f1e700:~/fruits#
```
### **3. `tail`**

The `tail` command is the reverse of `head`, returning the lines from bottom to top.

```bash

    root@537302f1e700:~/fruits# tail list 
    mango                                                      
    banana                                                     
    oranges                                                    
    Melon                                                      
    mandarin                                                   
    Avocado                                                    
    coconut                                                    
    Cherry                                                     
    lime                                                       
    Longan                                                     
    root@537302f1e700:~/fruits# tail -3 list 
    Cherry                                                     
    lime                                                       
    Longan
```
### **4. `sort`**

The `sort` command is used to sort a file, arranging the records in a particular order.

```bash
    sort [options] path
    
    root@537302f1e700:~/fruits# sort list 
    1mango                                                     
    20melon                                                    
    3lime                                                      
    apple                                                      
    Avocado                                                    
    banana                                                     
    Cherry                                                     
    coconut
```
**Options with `sort` command:**

-   **-r**: Sorts in reverse order.
-   **-n**: Sorts the file numerically.
-   **-nr**: Sorts a file with numeric data in reverse order.
-   **-k**: Sorts the table based on any column.
-   **-c**: Checks if a given file is already sorted.
-   **-u**: Sorts and removes duplicates.
-   **-M**: Sorts a file on a monthly basis.

### **5. `uniq`**

The `uniq` command is used to remove duplicate lines. For example, in this case, `banana` was duplicated, and the `uniq` command removed the duplicate item.
```bash

    root@537302f1e700:~/fruits# cat list 
    apple                                                      
    mango                                                      
    banana                                                     
    banana                                                     
    oranges                                                    
    Melon                                                      
    mandarin                                                   
    Avocado                                                    
    coconut                                                    
    Cherry                                                     
    lime                                                       
    Longan                                                     
    1mango                                                     
    3lime                                                      
    20melo                                                     
    apple                                                      
    root@537302f1e700:~/fruits# uniq list 
    apple                                                      
    mango                                                      
    banana                                                     
    oranges
```
### **6. `wc`**

The `wc` command gives the number of lines, words, and characters in the data. By default, it displays four columnar outputs.


```bash
    root@537302f1e700:~/fruits# wc list 
     17  17 112 list

```

`wc [options] [path]` 

`wc` stands for word count.

With `wc`, you can pass more than one file.

**Note:** When more than one file is placed in the argument, it adds one more line that counts the total.

```bash

    root@537302f1e700:~/fruits# wc list melon orange 
     17  17 112 list                                           
      0   0   0 melon                                          
      0   0   0 orange                                         
     17  17 112 total
```
**`wc` options:**

-   **-l**: Prints the number of lines in a file.
-   **-w**: Prints the number of words in a file.
-   **-m**: Displays the count of characters in a file.
-   **-v**: Displays the version of `wc`.

**Some applications of the `wc` command:**

-   To count all the files and folders present in a directory: `ls list | wc -l`



`root@537302f1e700:~/fruits# ls list | wc -l 
1` 

-   To display the number of word count only of a file: `wc -w list`



`root@537302f1e700:~/fruits# wc -w list 
17 list` 

### **7. `grep`**

The `grep` command is used to search for particular information in a text file.


```bash
    grep [options] pattern [path]
    
    root@537302f1e700:~/fruits# grep banana list 
    banana
```
Or:


    root@537302f1e700:~/fruits# cat list | grep banana 
    banana

**`grep` options:**

-   **-v**: Displays names not matching the specified word.
-   **-i**: Filters output in a case-insensitive way.
-   **-A**: Displays a line after the result.
-   **-B**: Displays a line before the result.
-   **-C**: Displays a line before and after the result.

### **8. `nl`**

The `nl` command is used to print line numbers of the text file.

```bash

    nl [file-path]
    
    root@537302f1e700:~/fruits# nl list 
         1	apple                                               
         2	mango                                               
         3	banana                                              
         4	oranges                                             
         5	Melon                                               
         6	mandarin

```
```bash
    root@537302f1e700:~/fruits# cat -n list 
         1	apple                                               
         2	mango                                               
         3	banana                                              
         4	oranges                                             
         5	Melon                                               
         6	mandarin                                            
         7	Avocado                                             
         8	coconut                                             
         9	Cherry                                              
        10	lime                                                
        11	Longan                                              
        12	1mango                                              
        13	3lime                                               
        14	20melon                                             
        15	apple                                               
        16	mango                                               
        17	apple
 ```
**`nl` options:**

-   **-n**: To display the number and file.
-   **-s**: To display number padding with space.
-   **-b**: To display line numbers when the pattern matches.

**Some applications of `nl` command:**

-   To print a certain section of a file:



   
```bash
        root@537302f1e700:~/fruits# head -5 list | nl -b a 
             1	apple                                               
             2	mango                                               
             3	banana                                              
             4	oranges                                             
             5	Melon                                               
        root@537302f1e700:~/fruits# head -n 3 list | nl -b a 
             1	apple                                               
             2	mango                                               
             3	banana
```
## **Shell Expansions**

Shell expansion is the process of simplifying commands in order to get a return value from a shell prompt. The shell reads the command line and analyzes it to make it easier to understand.

The types of shell expansion include:

### **1. Pathname Expansion**

This is also known as "globbing." Pathname expansion is performed by the shell when it encounters a wildcard pattern (e.g., `*`, `?`, `[]`). These wildcards are replaced with a list of matching files and directories.

For example, `ls *.txt` would list all `.txt` files in the current directory.


```bash
    $ ls *.txt
    file1.txt file2.txt file3.txt
```
### **2. Tilde Expansion**

When the shell encounters a tilde (`~`), it expands it to the current user's home directory.

For example, `cd ~` would change the directory to the user's home directory.
```bash

    $ echo ~
    /home/username
```
### **3. Arithmetic Expansion**

Arithmetic expansion allows the evaluation of an arithmetic expression and its substitution into the command.

For example, `echo $((2 + 2))` would output `4`.

```bash

    $ echo $((2 + 2))
    4
```
### **4. Command Substitution**

Command substitution allows the output of a command to replace the command itself. This is done using backticks (`) or `$(...)`.

For example, `echo "Today is $(date)"` would output the current date.


    $ echo "Today is $(date)"
    Today is Mon Aug 28 10:37:26 UTC 2024

### **5. Brace Expansion**

Brace expansion is used to generate arbitrary strings. It is typically used for creating multiple similar files or directories at once.

For example, `echo file{1..3}.txt` would output `file1.txt file2.txt file3.txt`.

```bash

    $ echo file{1..3}.txt
    file1.txt file2.txt file3.txt
```
### **6. Variable Expansion**

Variable expansion allows the value of a variable to replace the variable name.

For example, if `NAME="John"`, then `echo "Hello, $NAME"` would output `Hello, John`.

```bash
    $ NAME="John"
    $ echo "Hello, $NAME"
    Hello, John 
```
## **Conclusion**

Learning about I/O redirection, shell filters, and shell expansion is essential for effective command-line usage. These features allow for powerful text manipulation and automation, enabling users to work more efficiently with files, processes, and data in a Linux environment. By mastering these concepts, you will be better equipped to harness the full potential of the command line and streamline your workflow.