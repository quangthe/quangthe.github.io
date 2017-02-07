---
layout: post
title: Edit readonly file using VIM editor
---

The following tips will help edit and save readonly text file using VIM editor

![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/Icon-Vim.svg/256px-Icon-Vim.svg.png "VIM editor")

Create empty file

```bash
$ touch readonly.txt
```

Add some content

```bash
$ echo "Readonly Text" > readonly.txt
```

Make it read-only

```bash
$ chmod 444 readonly.txt
```

Try to edit it

```bash
$ vim readonly.txt

Readonly content

~                                                    
~                                                    
"readonly.txt" [readonly] 2L, 18C  1,1           All
```

Press Shift + : to enter command mode

Enter command: **w !sudo tee %**

```bash 
Readonly content

~                                                    
~                                                    
:w !sudo tee %
```

What the command does:

* :w = Write a file.
* !sudo = Call shell sudo command.
* tee = The output of the vi/vim write command is redirected using tee.
* % = Triggers the use of the current filename.
* Simply put, the ‘tee’ command is run as sudo and follows the vi/vim command on the current filename given.
