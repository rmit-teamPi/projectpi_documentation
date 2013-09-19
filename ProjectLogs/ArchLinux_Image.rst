--------------
Arch Linux Arm
--------------

- Resizing:
   Note: Where '>>' is shown, enter the command shown followed by the "RETURN/ENTER" key.
   
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

   ...

   # resize2fs /dev/mmcblk0p5

- Set the hostname:
    # echo "hostname" > /etc/hostname

- WiFi:
    **To Connect:**

    # wifi-menu -o

    --> Pick network to connect.

    **To Auto Connect:**

    # netctl list

    # cp /etc/netctl/wlan0-*** /etc/netctl/<profile>

    # netctl start <profile>

    # netctl enable <profile>
    
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
    # useradd -m <username>

    # passwd <username>

    # groupadd admin

    # gpasswd -a <username> admin

- Install:
    1) Sudo:
    
        - Install "sudo" using package manager (pacman)
        # pacman -S sudo
    
        - Give "admin" group sudo rights.
        
            # visudo

            Find "#%wheel ALL=(ALL) ALL". Change it to:
            
            %admin ALL=(ALL) ALL
    2) Vim
    3) Git
    4) Python 2 & 3
    
        # pacman -S python2
        
        # pacman -S python3
    5) GCC
    
        # pacman -S gcc
    6) OpenMPI
    
        # pacman -Syy openmpi

