-------------------------
Setting up Arch Linux ARM
-------------------------

- Resizing:

  ::

     # fdisk /dev/mmcblk0

       >> p
       
       >> d
       
       >> 2
       
       >> n
       
       >> e
       
       >> (return) = accept default partition number
       
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

- Set the timezone:

   ``# ln -s /usr/share/zoneinfo/Australia/Melbourne /etc/localtime``

- Update System:

   ``# pacman-key --init``

   Press (Alt+F2) to switch to a 2nd virtual console, then enter the following command:

   ``# ls -R / && ls -R / && ls -R /``

   Press (Alt+F1) to swtich back 1st virtual console.
   Check whether the "pacman-key --init" command has finished running.

   ``# pacman -Syu``

- Users and Groups:

   **Note:** Use the following credentials when executing the steps below:
   
        Username: rpicluster
   
        Password: rpicluster

  ::
      
      # useradd -m <username>

      # passwd <username>

      # groupadd admin

      # gpasswd -a <username> admin


- Install the following using Arch Linux's package manager (pacman).
    
    1. **Sudo:**
       
       ``# pacman -S sudo``
    
       - Give "admin" group sudo rights.

       ``# visudo``

       Find "#%wheel ALL=(ALL) ALL". Change it to:
          
       ``%admin ALL=(ALL) ALL``

    2. Vim:
        ``# pacman -Syy vim``
    3. GCC:
        ``# pacman -Syy gcc``
    4. Make:
        ``# pacman -Syy make``
    5. OpenMPI:
        ``# pacman -Syy openmpi``
    6. OpenSSH:
        ``# pacman -Syy openssh``
    7. NFS:
        ``# pacman -Syy nfs-utils``

