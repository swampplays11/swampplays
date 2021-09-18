---
description: >-
  Make a trash command in bash, which sends files to a recyle bin, instead of
  deleting them.
---

# Bash - Trash Command

For the solution, we will separate each task into separate commands, and then [combine](bash-trash-command.md#bonus-make-command-executable) then into one trash command.

## Move Files Into Trash Folder

### Make Trash Folder

In the default directory, we will make a directory for storing trash, then a directory for storing logs.

```bash
$ mkdir ~/trash ~/logs
```

### Move Items to Trash

This will move a file to trash. We will [make this configurable](bash-trash-command.md#bonus-make-command-executable) later.

```bash
$ mv file_name.txt ~/trash
```

## Log Actions in a File

### Add a Timestamp

This will return a timestamp in the format: **HH:MM:SS**.

```bash
$ date | cut --delimiter " " --fields 4
13:37:13
```

### Log Files

```bash
$ date 1>> timestamp
```

[https://help.codea.live/raspberry-pi-hosting/challenges\#challenge-make-a-trash-command](https://help.codea.live/raspberry-pi-hosting/challenges#challenge-make-a-trash-command)

## \[Bonus\] Make It a Script

### Add Script to PATH

```bash
$ 
$ mkdir ~/bin
```

{% code title="~/bin/trash" %}
```bash
$FILE_NAME=""

```
{% endcode %}

{% embed url="https://askubuntu.com/questions/60218/how-to-add-a-directory-to-the-path" %}

