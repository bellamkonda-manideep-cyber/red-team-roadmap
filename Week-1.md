Day-1 :- Setup & Orientation.

1. Just create a free account in TryHackMe and HackTheBox.
  
2. Download and install virtualzation software: VirtualBox/ VMware Workstation Player.
   
3. Download & install a pentesting distro: [Install Kali Linux](https://www.kali.org/get-kali/#kali-platforms)
   
4. Install AlmaLinux 10 (Red Hat–compatible) VMware: [Install ALmaLinux](https://almalinux.org/get-almalinux/)
   
5. Learn basic commands (docs): [commands](https://linuxcommand.org/lc3_learning_the_shell.php)
                                Commands: whoami, id, pwd, ls -la, uname -a, cat /etc/os-release
   

Day-2 :- Linux Fundamentals (core shell)

1. Do Linux Fundamentals Part 1 – [TryHackMe](https://tryhackme.com/room/linuxfundamentalspart1)
   
2. Core concepts: [Understanding core concepts](https://ryanstutorials.net/linuxtutorial/) 
   

Day-3 :– Permissions & Ownership

1. Learn permissions: read (r), write (w), execute (x).

2. Commands: chmod, chown, chgrp, umask.

3. Practice: create a file, restrict access, test with another user.

Resources :- [File Permissions](https://www.tutorialspoint.com/unix/unix-file-permission.htm)


Day-4 :– Users & Groups

1. Create new users: useradd, passwd.

2. Manage groups: groupadd, usermod -aG.

3. Switch users: su, sudo.

Resources :- [Users and Groups](https://labex.io/lesson/users-and-groups)


Day-5 :– Process Management & Services

1. Commands: ps, top, htop, kill, systemctl, journalctl.

2. Start/stop services: systemctl start sshd.

3. Check logs with journalctl.
   
Resources :- [Systemd](https://wiki.archlinux.org/title/Systemd), [YouTube Video for Systemd](https://www.youtube.com/watch?v=Kzpm-rGAXos)

Day-6 :- Networking Basics

1. Learn IP commands: ip addr, ip route, ping, traceroute.

2. Check open ports: ss -tulnp.

3. Configure static IP inside VM (lab)

Resources :- [IP Command Examples](https://www.tecmint.com/ip-command-examples/), [Cisco Networking Basics Course](https://www.netacad.com/courses/networking-basics?courseLang=en-US)


Day-7 :- Shell Scripting Basics

1. Write a script to:

    Create a user.

    Make a backup of /etc/passwd.

   Append date/time to a log file.

Learn about shebang (#!/bin/bash).

Resources :- [Bash Scripting](https://ryanstutorials.net/bash-scripting-tutorial/), [YouTube Video for Bash Scripting](https://www.youtube.com/watch?v=e7BufAVwDiM)


At the end of Week 1, we will:

  --> Be comfortable in Linux CLI.

  --> Know file permissions, users, groups, services.

  --> Understand networking commands.

  --> Write simple shell scripts.
