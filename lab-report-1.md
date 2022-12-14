
# Week 1 Lab Report
---

## How to use ssh, scp, and some basics

 
**1) Installing ~~VS CODE~~ VS-CODIUM**

While VS-Code is still open source, it is created for purposes intended by microsoft.

Get rid of the telemetry. Install VS-Codium

On my system: `sudo pacman -S vscodium-bin` (We're not compiling it ourself.)

I'm not downloading it again so I'm using `pacman -Qi vscodium` to just read some stuff.

![Image](images/vscodium.png)

As it says under its package information it is basically vscode.

VS Code is very customizable. It has a lot of plug ins that enhance your programming experience. (Like the vim keybinding extension I currently have). One small change you can make is going to file>preferences>color theme. This will set a theme for the application. Since I also code in daylight and I needed a good light mode so I changed it to look like this:

![Image](images/vs_snapshot.png)

 
**2) Remotely Connecting (ssh)**

Obviously we want to establish an ssh connection. This "secure shell" is done by writing out `ssh <user>@<hostname>`. That should be it most of the time. I did the same thing when I was logging into my rasberry pi once too. Perfectly fine. In this case our user would be cs15lfa22zz or something similar because that is the username for the class. And hostname on the UCSD cluster is ieng6.ucsd.edu. You can get <user> with `whoami` and <hostname> with `hostname` commands. 

You can find more about your user [here](https://sdacs.ucsd.edu/~icc/index.php)
Make sure to reset your password!

So remoting into my user would look like `ssh cs15lfa22ca@ieng6.ucsd.edu`

It will ask you if you want to continue connecting only the first time you ssh.


![Image](images/sshing_into_user.png)


**3) Trying some commands (cmon I know this)**
    
I know some of the basic commands. I know that `cd`, `mkdir`, `rmdir`, `mv`, etc. I use them almost every day. But maybe I'll list some of my favorite info.
Adding the "-l" flag to ls is more likeable if I want information on permssions and time. 
The "find" command is very helpful to search. Usually I use it as `find <path_parent> -name <file_name>`
And of course the grep command. The command gives me a line with the expression I am looking for. Like `grep <file_name> <regex_expression>`

And of course there are a lot of other commands. And shortcuts like using :s/.../../ or maybe !* or !<number>.

![Image](images/bash_commands.png)


**4) Moving files with scp**

ftp stands for file transfer protocol. scp only stands for just secure copy. Here I thought the p in scp stood for protocol too...

Anyways, to use it's pretty obvious how. 
Just use `scp <target_file> <user>@<hostname>:<file_path/file_name>`

That's all it is. Make sure to specify the file path location! I had a friend of mine not  have it work because he left the area after the colon blank. Also to copy something from host to client just reverse the order of the arguements. Easy!

As an example we will create "WhereAmI.java" on our host computer, then use scp to send it to the remote computer.

![Image](images/ssh-scp.png)

**5) Setting a ssh key**
 
So of course we don't want to have to enter our password. I didn't figure this out when I used the rasberry pi. Small brain.

Before you continue you will need to have the ".ssh" directory in your host home directory. So ssh into your account, then `mkdir .ssh`. Having a '.' as the first character in a file on linux isn't just convention, it also makes the file/directory "hidden". Most times it won't appear unless you specify some flags to show it.

Basically on my client I will run `ssh-keygen` which generates a key. Running it I see it places it under my own "~/.ssh/". We are interested in using the public key, so the file named "id_rsa.pub" or something like that.

Anyways, we will secure copy the .pub file and place the contents of this file in our remote computer. We use scp again but this time place it in "~/.ssh/authorized_keys". Since we're just allowing only one user we can just place 'id_rsa' into '.ssh/' directory and rename it to 'authorized_keys'.
    
![Image](images/ssh_authorized_keys.png)




**6) Optimize, configure. We are the linux user.**
 
It is our destiny. We optimize and configure. We tweak to our needs and wants. We are the linux user.

Something I did not know was speicifying a command after ssh by including another argument in the form of paranthesis. 
For example typing out `ssh cs15lfa22ca@ieng6.ucsd.edu "mkdir .ssh"` will try to create the ".ssh" directory and log out. This is very helpful as we could of used it earlier when we were setting the ssh key without having to log out since it would of been automatic. (It would of logged in, run the command, and exit).

Oh and well, there tricks to running commands. Having `command1 ; command2` will run the second command after the first. `command1 && command2` is a conditional statement where the second runs only if the first succeeds. And `command1 || command2` runs command2 only if command1 fails. Very nice to have small tricks like that. In fact in the picture below we make use of `ssh` with inputting a string of two commands seperated by ";", having our terminal first `ls` then `echo`.

![Image](images/lab1-tricks.png)

**7) Extra**


TWEAK IT. TWEAK IT.
CHANGE THE RC HAHAHAHAHA.

Files like ".bash_profile" ".bashrc" are files in the home directory that run when a new terminal opens up. In this case it looks like changing the .bashrc isn't sourcing properly after every session. However! '.bash_profile' is. So I have put some commands that I want to run automatically when I enter a session.

This is helpful if you want to Run Commands on starting it up. Like setting configurations and such. Here are some of mine.


`set -o vi` gives vi keybindings in terminal.
`export PATH="<newpath>:$PATH"` gives a new path to search for more programs.
`export PS1="blah blah $ ` gives a new prompt when shell is successful
`export PS2="no please $ ` gives this prompt when shell fails.

There are more things I would like to set, but this is just one small idea of what can be changed.

![Image](images/custom_bash_profile.png)




[Link back](index.md)
