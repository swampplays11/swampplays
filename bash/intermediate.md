---
description: >-
  More advanced bash concepts like piping, aliases, and more explained in one
  guide.
---

# Bash Intermediate

{% hint style="info" %}
This content is from an upcoming [Raspberry Pi hosting course](../raspberry-pi-hosting/overview.md).
{% endhint %}

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

## [Challenge - Make a Today Command](../raspberry-pi-hosting/challenges/#challenge-make-a-trash-command)

{% hint style="success" %}
Doing is the most effective way of learning, and will help reinforce your knowledge and understanding.
{% endhint %}

### References

{% hint style="info" %}
This content is from an upcoming [Raspberry Pi hosting course](../raspberry-pi-hosting/overview.md).
{% endhint %}

