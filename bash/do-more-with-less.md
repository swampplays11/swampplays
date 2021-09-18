---
description: >-
  More advanced bash concepts like piping, aliases, and more explained in one
  guide, that will help you save time and energy.
---

# Bash - Do More With Less

## In This Guide...

{% hint style="success" %}
**After this guide you will**:

* Be more efficient with the bash shell.
* Know how to [execute previous bash commands](do-more-with-less.md#time-travel-bash-history).
* Know how to [clear bash command history](do-more-with-less.md#how-to-clear-bash-history).
* Know how to shortern commands with [aliases](do-more-with-less.md#shorten-commands-bash-aliases).
* Know how to [customize the terminal colours](do-more-with-less.md#customize-the-terminal-command-prefix).
* Know how to [create patterns](do-more-with-less.md#wildcards) to match file and folder names.
* Be able to create [bash pipelines](do-more-with-less.md#piping) to do more with less.
* Know how to [execute multiple commands with one command](do-more-with-less.md#brace-expansion).
* Reinforce your knowledge with a [quick challenge](do-more-with-less.md#challenge-make-a-today-command).
{% endhint %}

{% hint style="success" %}
**Prerequisites**: [know the basics of bash](basics.md).
{% endhint %}

{% hint style="info" %}
This content is from the [Complete Raspberry Pi 24/7 Hosting Course](https://bit.ly/raspberry-pi-hosting).
{% endhint %}

## Time Travel - Bash History

Here you will learn how to go back in time and execute previous commands. This is how....

#### The history command lets us see previously executed commands.

```bash
$ history
    1  ls
    2  echo "Testing123"
    3  ls
    4  history
```

We can then execute them with `!<command_number>`.

```bash
$ !2
echo Testing123
Testing123
```

### How to Clear Bash History

Sometimes history may get messy, and mine had 500+ previous commands, before making this tutorial.

#### Syntax

```bash
$ history -c; history -w;
```

{% hint style="info" %}
`.bash_history` stores bash history.
{% endhint %}

## .bashrc

> `.bashrc` is a Bash [shell script](http://en.wikipedia.org/wiki/Shell_script) that Bash runs whenever it is started interactively.

{% embed url="https://unix.stackexchange.com/questions/129143/what-is-the-purpose-of-bashrc-and-how-does-it-work" %}

Hence when .bashrc looks like this...

{% code title="~/.bashrc" %}
```bash
echo "Testing123"
```
{% endcode %}

Then we reload the terminal with `bash` we get this...

```bash
$ adam@adam-desktop:~$ bash
Testing123
```

#### Every time the bash terminal is loaded, `.bashrc` is executed.

### Customize the Terminal - Command Prefix

`.bashrc` can be used for many things including **customizing** the bash **command** **prefix**.

This is how I did it:

{% code title="~/.bashrc" %}
```bash
PS1='[\033[1;31m]\u[\033[m]@[\033[1;32m]\h[\033[m]:[\033[1;36m]\w[\033[m]$[\033[m] '
```
{% endcode %}

![Now the prefix has colours!](../.gitbook/assets/image%20%2846%29.png)

## Shorten Commands - Bash Aliases

```bash
alias <name>="<command>"
```

#### Example

{% code title="~/.bashrc" %}
```bash
alias testing123="echo 'It Worked!'"
```
{% endcode %}

```bash
$ bash # or manually reopen the terminal
$ testing123
It Worked!
```

### Use .bash\_aliases for aliases

In the **default folder** \(`~`\), we can create **special file** called `.bash_aliases`. This is a conventional file to contain bash aliases. 

This is optional, but the code in `.bashrc` below should load the aliases in the file.

{% code title="~/.bashrc" %}
```bash
if [ -f $HOME/.bash_aliases ]
then
  . $HOME/.bash_aliases
fi
```
{% endcode %}

## Wildcards

Wildcard characters are used to define **patterns** for searching text on data in bash.

{% hint style="info" %}
The find command is used for finding files or folders within a folder.  
Type `man find` for more info.
{% endhint %}

### Grep - Match Patterns in Strings

The code below will find the line containing `'-e '`, and output it.

```bash
$ man grep | grep -e '-e '
```

### Anything - Star or Asterisk \(\*\)

Used to search for any character, zero or more times.

{% tabs %}
{% tab title="Example 1" %}
This will find everything in the current directory.

```bash
$ find *
1.txt
2.txt
3.txt
a.png
b.png
c.png
error.log
log.log
log.txt
20-04-21-213100.log
```
{% endtab %}

{% tab title="Example 2" %}
This is also useful if you want to find anything that matches a file extension.

```bash
$ find *.png
```
{% endtab %}

{% tab title="Example 3" %}
This is used to find a file with a specific name and any file extension.

```bash
$ find log.*
log.log
log.txt
```
{% endtab %}
{% endtabs %}

### Unknown - Question Mark \(?\)

Used to search for a fixed number of characters. '?' can indicate an unknown character.

{% tabs %}
{% tab title="Example 1" %}
This will find any .txt file with a 1 character name.

```bash
$ find ?.txt
1.txt
2.txt
3.txt
```
{% endtab %}

{% tab title="Example 2" %}
This will find any file name, with a 3 letter file extension, with 'x' in the middle.

```bash
$ find *.?x?
1.txt
2.txt
3.txt
log.txt
```
{% endtab %}

{% tab title="Example 3" %}
In this example, this operator can be useful for finding log files at a specific hour.

```bash
$ find 20-04-21-21????.log
20-04-21-213100.log
```
{% endtab %}
{% endtabs %}

### Range - Square Brackets \(\[\]\)

Used to search for a range of characters \(i.e. 0-9, a-z\).

{% hint style="info" %}
Ranges are case sensitive. Therefore, `[a-z]` will not match 'Z', but `[A-Z]` will.
{% endhint %}

{% tabs %}
{% tab title="Example 1" %}
This is useful for finding files that start with any number from 0-9. This is called a **range**.

```bash
$ find [0-9].txt
1.txt
2.txt
3.txt
```
{% endtab %}

{% tab title="Example 2" %}
This also works with the alphabet!

```bash
$ find [a-z].png
a.png
b.png
c.png
```
{% endtab %}

{% tab title="Example 3" %}
The square bracket can combine characters to make a **set**. The character can only be any character within the set. 

```bash
$ find [23ac].???
2.txt
3.txt
a.png
c.png
```
{% endtab %}
{% endtabs %}

## Piping

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

## Brace Expansion

Brace expansion is used to generate strings.

{% tabs %}
{% tab title="Combinations" %}
```bash
$ echo {a..z}
a b c d e f g h i j k l m n o p q r s t u v w x y z
$ echo {z..w}
z y x w
$ echo {1..10}
1 2 3 4 5 6 7 8 9 10
$ echo {3..-1}
3 2 1 0 -1
```
{% endtab %}

{% tab title="Prefix/Suffix" %}
```bash
$ echo a{a..f}
aa ab ac ad ae af
$ echo {1..3} && echo {99,100}
1 2 3 99 100
```
{% endtab %}

{% tab title="List Command Example" %}
```bash
$ ls {Desktop,Documents}
Desktop:
'Visual Studio Code.lnk'*   desktop.ini

Documents:
'My Music'@  'My Pictures'@  'My Videos'@   desktop.ini
```
{% endtab %}
{% endtabs %}

### Nested Brace Expansion

```bash
$ echo {a,{a..c},{a..c}}
a a b c a b c
```

{% hint style="warning" %}
Make sure there are no spaces around commas, otherwise brace expansion will not work.
{% endhint %}

### Multiple Brace Expansion

_Brace_ yourself for a basic maths lesson.

$$
3^2=3*3=9
$$

```bash
$ echo {1..3} # 3*1 = 3 combinations
1 2 3
$ echo {1..3}{1..3} # 3*3 = 9 combinations
11 12 13 21 22 23 31 32 33
$ echo {1..3}{1..3}{1..3} # 3*3*3 = 27 combinations
111 112 113 121 122 123 131 132 133 211 212 213 221 222 223 231 232 233 311 312 313 321 322 323 331 332 333
```

## [Challenge - Make a Today Command](../raspberry-pi-hosting/challenges/#challenge-make-a-trash-command)

{% hint style="success" %}
Doing is the most effective way of learning, and will help reinforce your knowledge and understanding.
{% endhint %}

{% hint style="info" %}
This content is from an upcoming [Raspberry Pi hosting course](../raspberry-pi-hosting/overview.md).
{% endhint %}

