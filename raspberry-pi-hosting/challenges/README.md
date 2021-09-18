---
description: Practical challenges and solutions from the Raspberry Pi hosting course.
---

# Challenges

Here are some challenges from the Raspberry Pi hosting course. They are intended to be practical in the real world, and I personally some of the solutions with my PC.

{% hint style="info" %}
Doing is the most effective way of learning, and will help reinforce your knowledge and understanding.
{% endhint %}

## Challenge - Make a Clean Command

{% hint style="success" %}
### Test your knowledge and make a clean command.

**Purpose**: Organize Downloads and Pictures folders to prevent them from getting messy.  
**It Should**: Delete all files in Downloads, and move all screenshots into Pictures/screenshots.  
**Hint**: you should use the \* wildcard.

* [ ] Command should be on one line.
* [ ] Downloads and Pictures should be in the default directory \(**`~`**\).
* [ ] In this context, screenshots are any file that starts with 'Screenshot' 
  * Screenshots are created in Ubuntu 20.04 when you press **`prt sc`**.
{% endhint %}

## Challenge - Make a Today Command

{% hint style="success" %}
### Test your knowledge and make a today / reminder command.

**Purpose**: Write quick reminders for today, in folders that are organized by date.  
**It Should**: Create a .txt file in a path with a special format, then open it with a text editor.

* [ ] Command should be on one line.
* [ ] File path should be in the format: **log/ww/dd-mm.txt**
  * [ ] **ww** is the week number.
  * [ ] **dd** is the day number.
  * [ ] **mm** is the month number.
* [ ] Then open the file with a text editor \(i.e. Nano\).
{% endhint %}

## Challenge - Make a Trash Command

{% hint style="success" %}
### Test your knowledge and make a trash / recycle bin script.

**It Should**: Move a file to a trash folder, then append log of filename, and timestamp to a file.

* [ ] Command should be on one line.
* [ ] Each log should look like this: **\[13:37:01\] file.txt**
* [ ] Log file should be outside the trash folder.
{% endhint %}

### Solution

Once you are ready, you can look at the solution. Remember that there can be lots of solutions to one challenge, some better than others. 

{% page-ref page="bash-trash-command.md" %}



