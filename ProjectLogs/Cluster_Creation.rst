Cluster Configuration
=====================

- Set the hostname:

   **Note:** Enter the appropriate hostname for the device being setup
      
     +----------+---------------------------------------+
     | Device   | Command                               |
     +==========+=======================================+
     | masterpi | ``# echo "masterpi" > /etc/hostname`` |
     +----------+---------------------------------------+
     | slavepi0 | ``# echo "slavepi0" > /etc/hostname`` |
     +----------+---------------------------------------+
     | slavepi1 | ``# echo "slavepi1" > /etc/hostname`` |
     +----------+---------------------------------------+
     | slavepi2 | ``# echo "slavepi2" > /etc/hostname`` |
     +----------+---------------------------------------+
     | slavepi3 | ``# echo "slavepi3" > /etc/hostname`` |
     +----------+---------------------------------------+
     | slavepi4 | ``# echo "slavepi4" > /etc/hostname`` |
     +----------+---------------------------------------+

- SSH Configuration:

   OpenSSH setup is a core requirement for OpenMPI functionality.
   
   - **slavepiX ONLY:**
     
     - Follow the steps below for each of the slavepiX nodes.
   
     1) Generate an SSH Key Pair
   
        - Login as 'rpicluster'
      
        ::

            # sudo ssh-keygen -t rsa -b 2048 -C "$(whoami)@$(hostname)-$(date -I)"
               >> (return) = accept default save location
             
               >> (return) = accept default 'blank' passphrase
             
               >> (return) = confirm default 'blank' passphrase
   
     2) Copy SSH Keys from Slave Nodes
      
        ``# scp ~/.ssh/id_rsa.pub rpicluster@<hostname/ip address of masterpi>:``

   - **masterpi ONLY:**
   
     - Follow the steps below on the masterpi node.
     
    ::

         # mkdir ~/.ssh
         
         # cat ~/id_ecdsa.pub >> ~/.ssh/authorized_keys

         # rm ~/id_ecdsa.pub

         # chmod 600 ~/.ssh/authorized_keys

- NFS Configuration:

   - **Server Configuration [masterpi]**

     ``# sudo mkdir /cluster_shared``
   
     - Add the "cluster_shared" directory to NFS.
        
       ``# sudo vim /etc/exports``

         - Add the following line to the end of the file:
            
         ``\/cluster_shared     *(rw,sync)``
   
     ``# sudo chown -R nobody.nobody /cluster_shared``
   
     - Edit the "nfs-common.conf" file.
        
       ``# sudo vim /etc/conf.d/nfs-common.conf``

         - Find "STATD_OPTS=". Change it to:
            
         ``STATD_OPTS="-no-notify"``

   - **Client Configuration [slavepiX]**
   
     - Add the "cluster_shared" NFS share to the client.
     
       ``# sudo vim /etc/fstab``
       
         - Add the following line to the end of the file:
       
         ``172.20.32.82:/cluster_shared /cluster_shared nfs defaults 0 0``
       
   - **Server Configuration [masterpi]**
   
    ::

         # sudo systemctl enable sshd.service
         
         # systemctl is-enabled sshd.service
         
         # sudo systemctl enable nfsd.service
         
         # systemctl is-enabled nfsd.service
         
         # sudo systemctl enable rpcbind.service
         
         # systemctl is-enabled rpcbind.service
         
         # sudo systemctl enable rpc-idmapd.service
         
         # systemctl is-enabled rpc-idmapd.service
         
         # sudo systemctl enable rpc-mountd.serivce
         
         # systemctl is-enabled rpc.mountd.service
     
   - **Client Configuration [slavepiX]**
   
    ::

         # sudo systemctl enable sshd.service
         
         # systemctl is-enabled sshd.service
         
         # sudo systemctl enable rpcbind.service
         
         # systemctl is-enabled rpcbind.service
         
         # sudo systemctl enable rpc-idmapd.service
         
         # systemctl is-enabled rpc-idmapd.service
