# [Linux Upskill Challenge](https://github.com/livialima/linuxupskillchallenge)

> It is the mark of an educated mind to be able to entertain a thought without accepting it. --Aristotle

## Day0 - Creating Your Own Server with AWS Free Tier

Used my gmail account to create a free tier account in AWS, and launch the instance (all traffic, from anywhere) ![connecting](https://cdn-std.droplr.net/files/acc_498334/ntVSsj)

`ssh` connection: `ssh -i "keypair4linuxupskills.pem" ubuntu@ec2-18-117-241-98.us-east-2.compute.amazonaws.com`

Admin tasks:
`sudo apt update`
`sudo apt upgrade`
`logout` to exit.

### Extra Today

- Linux certification exams: LPIC, RHCSA, LFCS
- VPS: virtual private server
- KVM: kernel-based virtual machine
- ssh

## Day1 - Accessing Your Server

- [x] Connect and login to your server
- [x] Run a few simple commands to check the status of your server
- [ ] Change your password
- [x] `ssh` password-_less_

A few commands:

1. `lscpu`
2. `uptime`
3. `top` and `htop`
4. `free -h`
5. `df -h`
6. `lsblk`
7. `tree /home/`
8. `du -h`
9. `ncdu`
10. `netstat -i`
11. `ifconfig`
12. `ip addr`

Note: if the command is not installed, use `sudo apt install`

Useful link for setting up SSH config file and go password-_less_:

1. https://linuxize.com/post/using-the-ssh-config-file/
2. https://linuxize.com/post/how-to-setup-passwordless-ssh-login/

## Day2 - Basic Navigation

- [x] Use the provided resources to check out the basic commands and concepts
- [x] Login to your server via SSH and move about the directory structure at the command line
- [x] Take note of how your "prompt" changes as you change directory
- [x] Be sure to understand how `cd` on its own takes you back to your "home directory"
- [x] Understand what `cd ~` and `cd ..` do
- [x] Use the `ls` command to list the contents of directories, and try several of the "switches" - in particular `ls -ltr` to show the most recently altered file last
- [x] Use the `mkdir` command to create a new directory (folder) `test` in your home folder (e.g `/home/support/test`)

### Extenstions

- [x] Learn about `pushd` and `popd` to navigate around multiple directories easily.
  - [x] Running pushd /var/log moves you to to the /var/log, but keeps track of where you were. You can pushd more than one directory at a time. Try it out: pushd /var/log, pushd /dev, pushd /etc, pushd, popd, popd. Note how pushd with no arguments switches between the last two pushed directories but more complex navigation is also possible. Finally, cd - also moves you the last visited directory.
- [x] Take the time today to understand how the environment variable PS1 work.
  - [x] [Bash Shell: Take Control of PS1, PS2, PS4 and PROMPT_COMMAND](https://www.thegeekstuff.com/2008/09/bash-shell-take-control-of-ps1-ps2-ps3-ps4-and-prompt_command/)
- [x] Set yourself up with a custom prompt using the infomation in [Bash Shell PS1](https://www.thegeekstuff.com/2008/09/bash-shell-ps1-10-examples-to-make-your-linux-prompt-like-angelina-jolie/)
  - [x] The problem is that `.bashrc` is for non-login user only? What's the relationship between the bash config files?
    - In this case, it just need rebooting/reconnecting...

## Day3 - Power Trip!

- [x] Use the links in the "Resources" section below to understand how `sudo` works (refer to original repo for links)
- [x] Use `ls -l` to check the permissions of `/etc/shadow` - notice that only `root` has any access. Can you use `cat`, `less` or `nano` to view it?
- [x] This file is where the hashed passwords are kept. It is a prime target for intruders - who aim to grab it and use offline password crackers to discover the passwords.
- [x] Now try with `sudo`, e.g. `sudo less /etc/shadow`
- [x] Test running the `reboot` command, and then via `sudo` (i.e. `sudo reboot`)

Once you've reconnected back:

- [x] Use the `uptime` command to confirm that your server did actually fully restart
- [x] Test fully “becoming root” by the command `sudo -i` This can be handy if you have a series of commands to do "as root". Note the change to your prompt.
- [x] Type `exit` or `logout` to get back to your own normal login.
- [x] Use `less` to view the file `/var/log/auth.log`, where any use of `sudo` is logged. You could "filter" this by typing: `grep "sudo" /var/log/auth.log`

## Day4 - Installing software, exploring the file structure

- [ ] Install a new application from the online repositories
- [ ] Become familiar with some of the standard directories
- [ ] Look at the format and content of some configuration files

Try:

- `apt search midnight commander`
- `sudo apt install mc`
- `sudo apt install hier`
- How to play unix text game? `sudo apt install bsdgames` first.

## Day5 - More or Less...

- [x] Get familiar with using more and less for viewing files, including being able to get to the top or bottom of a file in less, and searching for some text

- [x] Test how “tab completion” works - this is a handy feature that helps you enter commands correctly. It helps find both the command and also file name parameters (so typing les then hitting “Tab” will complete the command less, but also typing less /etc/serv and pressing “Tab” will complete to less /etc/services. Try typing less /etc/s then pressing “Tab”, and again, to see how the feature handles ambiguity.

- [x] Now that you've typed in quite a few commands, try pressing the “Up arrow” to scroll back through them. What you should notice is that not only can you see your most recent commands - but even those from the last time you logged in. Now try the history command - this lists out the whole of your cached command history - often 100 or more entries. There are number of clever things that can be done with this. The simplest is to repeat a command - pick one line to repeat (say number 20) and repeat it by typing !20 and pressing “Enter”. Later when you'll be typing long, complex, commands this can be very handy. You can also press Ctrl + r, then start typing any part of the command that you are looking for. You'll see an autocomplete of a past command at your prompt. If you keep typing, you'll get more specific options appear. You can either run it by pressing return, or editing it first by pressing arrows or other movement keys.

  - `!!`: execute the last command; `sudo !!` to re-execute with root
  - `!80`: execute the 80th command in history; `!-1` == `!!`
  - `Ctrl-r`: reverse search the command history
  - history commands are stored in `~/.bash_history` file with setting in `~/bashrc` specifying `HISTSIZE` etc.

- [x] Look for “hidden” files in your home directory. In Linux the convention is simply that any file starting with a "." character is hidden. So, type cd to return to your "home directory" then ls -l to show what files are there. Now type `ls -la` or `ls -ltra` (the "a" is for "all") to show all the files - including those starting with a dot. By far the most common use of "dot files" is to keep personal settings in a home directory. So use your new skills with less to look at the contents of .bashrc , .bash_history and others.

- [x] Finally, use the nano/vim editor to create a file in your home directory and type up a summary of how the last five days have worked for you.
