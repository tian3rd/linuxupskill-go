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
