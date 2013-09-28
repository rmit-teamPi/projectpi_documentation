--------------
Arch Linux ARM
--------------

- Resizing:
   # fdisk /dev/mmcblk0

     >> p
     
     >> d
     
     >> 2
     
     >> n
     
     >> e
     
     >> (return) = accept default partition no
     
     >> (return) = accept default start
     
     >> (return) = accept default end
     
     >> n
     
     >> l
     
     >> (return) = accept default start
     
     >> (return) = accept default end
     
     >> p
     
     >> w

   # sync; reboot 

   # resize2fs /dev/mmcblk0p5

- Set the hostname:
   Note: Enter the appropriate hostname for the device being setup:
      
     +----------+-----------------------------------+
     | Device   | Command                           |
     +==========+===================================+
     | masterpi | # echo "masterpi" > /etc/hostname |
     +----------+-----------------------------------+
     | slavepi0 | # echo "slavepi0" > /etc/hostname |
     +----------+-----------------------------------+
     | slavepi1 | # echo "slavepi1" > /etc/hostname |
     +----------+-----------------------------------+
     | slavepi2 | # echo "slavepi2" > /etc/hostname |
     +----------+-----------------------------------+
     | slavepi3 | # echo "slavepi3" > /etc/hostname |
     +----------+-----------------------------------+
     | slavepi4 | # echo "slavepi4" > /etc/hostname |
     +----------+-----------------------------------+

- Set the timezone:
   # ln -s /usr/share/zoneinfo/Australia/Melbourne /etc/localtime

- Update System:
   # pacman-key --init

   Press (Alt+F2) to switch to a 2nd virtual console, then enter the following command:

   # ls -R / && ls -R / && ls -R /

   Press (Alt+F1) to swtich back 1st virtual console.
   Check whether the "pacman-key --init" command has finished running.

   # pacman -Syu

- Users and Groups:
   Note: Use the following credentials when executing the steps below:
   
   Username: rpicluster
   
   Password: rpicluster
      
    # useradd -m <username>

    # passwd <username>

    # groupadd admin

    # gpasswd -a <username> admin

- Install:
    Install the following using Arch Linux's package manager (pacman)
    
    1) Sudo:
    
       # pacman -S sudo
    
       - Give "admin" group sudo rights.
        
            # visudo

            Find "#%wheel ALL=(ALL) ALL". Change it to:
            
            %admin ALL=(ALL) ALL
    2) Vim
    
        # pacman -Syy vim
    3) GCC
    
        # pacman -Syy gcc
    4) Make
    
        # pacman -Syy make
    5) OpenMPI
    
        # pacman -Syy openmpi
    6) OpenSSH
    
        # pacman -Syy openssh
    7) NFS

        # pacman -Syy nfs-utils

- SSH Configuration:
   OpenSSH setup is a core requirement for OpenMPI functionality.
   
   1) Generate an SSH Key Pair
      
      - Run the following command on all clients
       
       # ssh-keygen -t rsa -b 2048 -C "$(whoami)@$(hostname)-$(date -I)"
