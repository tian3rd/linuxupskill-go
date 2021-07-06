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

## Day6 - Editing with "vim"

`:%s/old/new/gc`:

- `:`: enter command mode
- `%`: go to match in all lines
- `s`: substitute
- `/`: find
- `old` and `new`: old words to be replaced with new words
- `g`: global
- `c`: confirm before replacing

[Graphical vi-vim Cheat Sheet and Tutorial](http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html)

## Day7 - Installing Apache

- [x] Refresh your list of available packages (apps) by: `sudo apt update` - this takes a moment or two, but ensures that you'll be getting the latest versions.
- [x] Install Apache from the repository with a simple: `sudo apt install apache2`
- [x] Confirm that it’s running by browsing to http://[external IP of your server where you should see a confirmation page.
  - notice that it's `http` instead of `https`
- [x] Apache is installed as a "service" - a program that starts automatically when the server starts and keeps running whether anyone is logged in or not. Try stopping it with the command: `sudo systemctl stop apache2` - check that the webpage goes dead - then re-start it with `sudo systemctl start apache2` - and check its status with: `systemctl status apache2`.
- [x] As with the vast majority of Linux software, configuration is controlled by files under the /etc directory - check the configuration files under /etc/apache2 especially /etc/apache2/apache2.conf - you can use less to simply view them, or the vim editor to view and edit as you wish.
- [x] In /etc/apache2/apache2.conf there's the line with the text: "IncludeOptional conf-enabled/_.conf". This tells Apache that the _.conf files in the subdirectory conf-enabled should be merged in with those from /etc/apache2/apache2.conf at load. This approach of lots of small specific config files is common.
- [ ] If you're familiar with configuring web servers, then go crazy, setup some virtual hosts, or add in some mods etc.
- [x] The location of the default webpage is defined by the DocumentRoot parameter in the file /etc/apache2/sites-enabled/000-default.conf.
- [x] Use less or vim to view the code of the default page - normally at /var/www/html/index.html. This uses fairly complex modern web design - so you might like to browse to http://54.147.18.200/sample where you'll see a much simpler page. Use View Source in your browser to see the code of this, copy it, and then, in your ssh session sudo vim /var/www/html/index.html to first delete the existing content, then paste in this simple example - and then edit to your own taste. View the result with your workstation browser by again going to http://[external IP of your server]
  - [ ] What's the difference/relation between a public IPv4 address and IPv6? I used `ifconfig` to find the addresses, but it doesn't show my IPv4 address.
- [x] As with most Linux services, Apache keeps its logs under the /var/log directory - look at the logs in /var/log/apache2 - in the access.log file you should be able to see your session from when you browsed to the test page. Notice that there's an overwhelming amount of detail - this is typical, but in a later lesson you'll learn how to filter out just what you want. Notice the error.log file too - hopefully this one will be empty!

## Day8 - The Infamous "grep"

- [x] Dump out the complete contents of a file with cat like this: cat /var/log/apache2/access.log
- [x] Use less to open the same file, like this: less /var/log/apache2/access.log - and move up and down through the file with your arrow keys, then use “q” to quit.
- [x] Again using less, look at a file, but practice confidently moving around using gg, GG and /, n and N (to go to the top of the file, bottom of the file, to search for something and to hop to the next "hit" or back to the previous one)
- [x] View recent logins and sudo usage by viewing /var/log/auth.log with less
- [x] Look at just the tail end of the file with tail /var/log/apache2/access.log (yes, there's also a head command!)
- [ ] Follow a log in real-time with: tail -f /var/log/apache2/access.log (while accessing your server’s web page in a browser)
- [x] You can take the output of one command and "pipe" it in as the input to another by using the | (pipe) symbol. So, dump out a file with cat, but pipe that output to grep with a search term - like this: cat /var/log/auth.log | grep "authenticating"
- [x] Simplify this to: grep "authenticating" /var/log/auth.log
- [x] Piping allows you to narrow your search, e.g. grep "authenticating" /var/log/auth.log | grep "root"
- [x] Use the cut command to select out most interesting portions of each line by specifying "-d" (delimiter) and "-f" (field) - like: grep "authenticating" /var/log/auth.log| grep "root"| cut -f 10- -d" " (field 10 onwards, where the delimiter between field is the " " character). This approach can be very useful in extracting useful information from log data.
- [x] Use the -v option to invert (not "root" in the following example) the selection and find attempts to login with other users: grep "authenticating" /var/log/auth.log| grep -v "root"| cut -f 10- -d" "

### Extenstions

- [x] See if you can extend your filtering of auth.log to select just the IP addresses, then pipe this to sort, and then further to uniq to get a list of all those IP addresses that have been "auditing" your server security for you.
  - `grep "root" /var/log/auth.log | grep -o "[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\│}" | sort | uniq > ~/attackers.txt`
- [ ] Investigate the awk and sed commands. When you're having difficulty figuring out how to do something with grep and cut, then you may need to step up to using these. Googling for "linux sed tricks" or "awk one liners" will get you many examples.
- [ ] Aim to learn at least one simple useful trick with both awk and sed

## Day9 - Ports, Open and Closed

- Port 22: ssh (config in `/etc/ssh/sshd_config`)
- Port 23: telnet
- Port 80: http
- Port 53: dns

`ss`: socket status is a tandard utility replacing old `netstat`, use `ss -ltpn` to check status
`nmap`: port scanner; use `ip a` to find the IP of your actural network card, and the `nmap` that
`ufw`: firewall functionality for `iptables` and `nftables`

- `sudo iptables -L`
- Apply some rules: allow `ssh` and deny `http`, afterwards your AWS public ipv4 address via `http`(not `https`) will drop all incoming traffic so it's not accessible from outside though it's still running locally:
  - `suo ufw allow ssh`
  - `sudo ufw deny http`
  - `sudo ufw enable`
- To reverse, add the followings:
  - `sudo ufw allow http`
  - `sudo ufw enable`

## Day10 - Scheduling

- [ ] Look at the articles in the resources section - you should be aware of at and anacron but are not likely to use them in a server.

- [ ] Google for "logrotate", and then look at the logs in your own server to see how they've been "rotated".

- Each user potentially has their own set of scheduled task which can be listed with the crontab command (list out your user crontab entry with `crontab -l` and then that for root with `sudo crontab -l` )
- Use `sudo vim /etc/crontab` to view system-wide settings. `ls /etc/cron.daily` to view daily tasks
- Use `systemctl list-timers` to view system-wide schedules.

## Day11 - Finding Things...

- `which`
- `find`: `sudo find /var -name access.log`, `sudo find /home -mtime -3`
- `locate`: use `sudo apt install mlocate` to install `locate` and update the database for it with `sudo updatedb`, then search with `locate access.log`
- `grep`: `sudo grep -R -i "permitRootLOGIn" /etc/*`

### Extenstions

- [ ] `find` examples and tricks
