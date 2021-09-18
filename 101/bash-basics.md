---
description: Get started with bash and learn maximize your efficiency with Linux!
---

# Bash Basics

{% hint style="info" %}
This content is from an upcoming [Raspberry Pi hosting course](../raspberry-pi-hosting/overview.md).
{% endhint %}

## How the Terminal Works

### What is the terminal?

The terminal, or command line interface \(CLI\), is a **program** that accepts **text** **input** to **execute** **functions**.

![](../.gitbook/assets/image%20%2842%29.png)

### What is a command?

A command is **text** in a **command** **line** that **executes** a **program**.  
Commands are simply programs.

`echo “Hello World”` is equal to `/usr/bin/echo “Hello World”`

![](../.gitbook/assets/image%20%2812%29.png)

### Command Anatomy - Prefix

![](../.gitbook/assets/image%20%2827%29.png)

### Command Anatomy - Command

![](../.gitbook/assets/image%20%2832%29.png)

### What is the PATH?

The PATH stores **where** commands are located - more specifically, all directories where they are found. This makes it easy for bash to find commands to be found by name, as it knows where to look.

```bash
$ echo $PATH
/usr/bin/node/bin:/home/adam/.local/bin:/home/adam/bin:/usr/bin/node/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```

{% hint style="info" %}
You may get different output, with different operating systems. Ubuntu 20.04 was used for this demo.
{% endhint %}

## man - The Command Manual

The **man**ual lets you find all you need to know about a _most_ commands.

### Syntax

```bash
$ man <command_name>
```

> "man is the system's manual pager. Each page argument given to man is normally the name of a program, utility or function. The manual page associated with each of these arguments is then found and displayed. A section, if provided, will direct man to look only in that section of the manual. The default action is to search in all of the avail‐ able sections following a pre-defined order \(see DEFAULTS\), and to show only the first page found, even if page exists in several sections."

— Manual page on the man command.

### What if the manual does not cover it?

The **help** command is available for some default bash commands.  
For example, **cd** does not have a manual page, and details info can be found with it.

```bash
$ help <command_name>
```

## Navigation - Show Files

### List Files

The **ls** command is used to **list** **files** in a directory.

```bash
adam@adam-MS-7B86:~/test$ ls
file.txt  hello.earth  testing.123
```

{% hint style="info" %}
When **opening** the **terminal**, the default user directory is denoted by the**`~`**symbol.  
In this case `~` refers to `/home/adam`. The **root** **user**, has **/root** as the default directory.
{% endhint %}

#### More Readable File List

The list command has arguments to make showing directory files easier to read. In this case, `-lh` refers to **list**, **human** **readable**. Type `man ls` to see more arguments.

```bash
adam@adam-MS-7B86:~/test$ ls -lh
total 8.0K
drwxrwxr-x 2 adam adam 4.0K Apr 12 18:49 files
-rw-rw-r-- 1 adam adam   12 Apr 12 18:31 file.txt
-rw-rw-r-- 1 adam adam    0 Apr 12 18:24 hello.earth
-rw-rw-r-- 1 adam adam    0 Apr 12 18:24 testing.123
```

### File Metadata

The **file** command is used to get the **metadata** of a file.

```bash
$ file file.txt
file.txt: Bourne-Again shell script, ASCII text executable
```

#### File Extensions Don't Matter!

In Linux, file extensions are not used by bash to determine the file type. Instead, the **data** inside the file is used to **determine** the file **type**. 

{% hint style="info" %}
`file.txt` is read as a shell script in Linux, and would be read as a text file on Windows.
{% endhint %}

## Navigation - Move Around

### pwd - Print Working Directory

The **pwd** command is used to **output** **where** the command is being executed in.

```bash
adam@adam-MS-7B86:~$ pwd
/home/adam
```

### cd - Change Directory

The **cd** command is used to change directory. In this case, we move from `~` to `~/test`. 

```bash
$ cd test
$ pwd
/home/adam/test
```

{% hint style="info" %}
Some directories, like `/root`, require **superuser** **permissions** to go there.  
You can type `sudo cd /root` to execute a command as the **superuser**.
{% endhint %}

## File Management - CRUD

**CRUD** stands for **C**reate, **R**ead, **U**pdate, **D**elete, and defines the **basic** **operations** for [file management](bash-basics.md#file-management-copy-and-move).

### Create - Files and Folders

```bash
$ touch <file_name>      # create an empty file
$ mkdir <file_name>         # create an empty directory
```

### Read - with Less

Less is a **terminal-based** **pager** in Linux that is used to **view** **text**, in pages.

```bash
$ less <file_name>
```

### Update - with Nano

While there are [many ways to update files](bash-basics.md#pipes-do-more-with-less), using Nano, a terminal-based text editor, can be quicker for more specific updates.

#### Syntax

Here is how to open a file with nano:

```bash
$ nano <file_name>
```

#### Nano Editor Preview

There are many keybinds with nano. Your editor may look something like this:

```javascript
  GNU nano 4.8                       file2.txt                                  

// type something here, then press
 'Ctrl + X', then 'Enter'
// on Windows to save




                                  [ New File ]
^G Get Help  ^O Write Out ^W Where Is  ^K Cut Text  ^J Justify   ^C Cur Pos
^X Exit      ^R Read File ^\ Replace   ^U Paste Text^T To Spell  ^_ Go To Line
```

{% hint style="info" %}
For more keybinds, you can check out this [nano cheatsheet](https://www.nano-editor.org/dist/latest/cheatsheet.html).
{% endhint %}

### Delete - Files and Folders

#### Syntax

```bash
$ rm <file_name>         # delete file(s)
$ rm -rf <file_name>     # 'recursive force' - delete folder(s) and contents 
```

{% hint style="warning" %}
`rm -rf` can be a dangerous command. Once a file is deleted, it cannot be recovered easily.
{% endhint %}

#### Safer Deletion

With the **interactive flag** you can more carefully delete files and folders, with a confirmation prompt.

```text
$ rm -i file.txt
rm: remove regular file 'file.txt'?
$ # type 'y' or 'n'
```

{% hint style="success" %}
The **trash** command can be made to make deletion safer. It's actually an [exercise](bash-basics.md#exercise-trash-command) at the end of this section.
{% endhint %}

## File Management - Copy and Move

### cp - Copy

The **cp** command is used to copy files, or directories, to another location. This duplicates the files/folders.

#### Syntax

```bash
$ cp file1.txt files
$ ls files
file.txt
```

Again, when **copying** **folders**, the `-r` \(**recursive**\) **flag** needs to be used.

### mv - Move

The **mv** command is used to move files or folders, to another location.  
This will remove the file/folder from the old location, and add it to the new location. 

#### Syntax

```bash
$ mv <old_path> <new_path>
```

#### Rename with the Move Command

The move command can also be used to **rename** files/folders.

```bash
$ mv file1.txt file2.txt
```

## Pipes - Do More With Less

### What is a pipeline?

In computer science, a pipeline is a **series** of **elements**, where each one is **connected** to the **next**.

![](../.gitbook/assets/image%20%2826%29.png)

### The Command Pipeline

```bash
$ echo "Hello Earth"
Hello Earth
```

**\[0\] Standard Input** - typed command and its arguments; stdin.  
**\[1\] Standard Output** - normal output from a command; stdout.  
**\[2\] Standard Error** - error output from a command; stderr.

![](../.gitbook/assets/image%20%2828%29.png)

### We Can Control Command Output

```bash
$ echo "Hello Earth" 0>> echo
$ Hello Earth
```

This command puts the output of the first command into the second command.

```bash
$ echo "Hello Earth" 1>> output.txt
$ cat output.txt
Hello Earth
```

This puts the output of the first command into a file \(output.txt\).

```bash
$ cat '' 2>> error.txt
$ cat error.txt
cat: '': No such file or directory
```

This puts the error from the cat command, into a file \(error.txt\).

### Logical Operators Can Help Too

Logical operators are used for command pipelines.

```bash
A ; B     # Run A and then B, regardless of success of A
A && B    # Run B if A succeeded
A || B    # Run B if A failed
A &       # Run A in background.
```

{% embed url="https://unix.stackexchange.com/questions/24684/confusing-use-of-and-operators" caption="More on Logical Operators" %}

## [Challenge - Make a Trash Command](../raspberry-pi-hosting/challenges/#challenge-make-a-trash-command)

{% hint style="success" %}
Doing is the most effective way of learning, and will help reinforce your knowledge and understanding.
{% endhint %}

## References

{% hint style="info" %}
This content is from an upcoming [Raspberry Pi hosting course](../raspberry-pi-hosting/overview.md).
{% endhint %}

