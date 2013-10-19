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

- Set a Static IP Address:

   **Note:** Enter the appropriate IP address for the device being setup
   
     +----------+---------------------------------------+
     | Device   | Command                               |
     +==========+=======================================+
     | masterpi | ``# sudo vim /etc/conf.d/network``    |
     |          |                                       |
     |          | | interface=eth0                      |
     |          | | address=172.20.32.82                |
     |          | | netmask=255.255.255.0               |
     |          | | broadcast=172.20.32.255             |
     |          | | gateway=172.20.32.1                 |
     +----------+---------------------------------------+
     | slavepi0 | ``# sudo vim /etc/conf.d/network``    |
     |          |                                       |
     |          | | interface=eth0                      |
     |          | | address=172.20.32.83                |
     |          | | netmask=255.255.255.0               |
     |          | | broadcast=172.20.32.255             |
     |          | | gateway=172.20.32.1                 |
     +----------+---------------------------------------+
     | slavepi1 | ``# sudo vim /etc/conf.d/network``    |
     |          |                                       |
     |          | | interface=eth0                      |
     |          | | address=172.20.32.84                |
     |          | | netmask=255.255.255.0               |
     |          | | broadcast=172.20.32.255             |
     |          | | gateway=172.20.32.1                 |
     +----------+---------------------------------------+
     | slavepi2 | ``# sudo vim /etc/conf.d/network``    |
     |          |                                       |
     |          | | interface=eth0                      |
     |          | | address=172.20.32.85                |
     |          | | netmask=255.255.255.0               |
     |          | | broadcast=172.20.32.255             |
     |          | | gateway=172.20.32.1                 |
     +----------+---------------------------------------+
     | slavepi3 | ``# sudo vim /etc/conf.d/network``    |
     |          |                                       |
     |          | | interface=eth0                      |
     |          | | address=172.20.32.86                |
     |          | | netmask=255.255.255.0               |
     |          | | broadcast=172.20.32.255             |
     |          | | gateway=172.20.32.1                 |
     +----------+---------------------------------------+
     | slavepi4 | ``# sudo vim /etc/conf.d/network``    |
     |          |                                       |
     |          | | interface=eth0                      |
     |          | | address=172.20.32.87                |
     |          | | netmask=255.255.255.0               |
     |          | | broadcast=172.20.32.255             |
     |          | | gateway=172.20.32.1                 |
     +----------+---------------------------------------+

   **Note:** Run the following on all nodes.

     ``# sudo vim /etc/systemd/system/network.service``
     
     | [Unit]
     | Description=Network Connectivity
     | Wants=network.target
     | Before=network.target
     |
     | [Service]
     | Type=oneshot
     | RemainAfterExit=yes
     | EnvironmentFile=/etc/conf.d/network
     | ExecStart=/sbin/ip link set dev ${interface} up
     | ExecStart=/sbin/ip addr add ${address}/${netmask} broadcast ${broadcast} dev ${interface}
     | ExecStart=/sbin/ip route add default via ${gateway}
     | ExecStop=/sbin/ip addr flush dev ${interface}
     | ExecStop=/sbin/ip link set dev ${interface} down
     |
     | [Install]
     | WantedBy=multi-user.target
     
     ``# sudo systemctl disable dhcpcd@eth0.service``
     
     ``# sudo systemctl enable network.service``
     

- SSH Configuration:

   OpenSSH setup is a core requirement for OpenMPI functionality.
   
   - **slavepiX ONLY:**
     
     *Follow the steps below for each of the slavepiX nodes.*
   
     1) Generate an SSH Key Pair
   
        > Login as 'rpicluster'
      
        ::

            # sudo ssh-keygen -t rsa -b 2048 -C "$(whoami)@$(hostname)-$(date -I)"
               >> (return) = accept default save location
             
               >> (return) = accept default 'blank' passphrase
             
               >> (return) = confirm default 'blank' passphrase
   
     2) Copy SSH Keys from Slave Nodes
      
        ``# ssh-copy-id -i ~/.ssh/id_rsa.pub rpicluster@172.20.32.82``

- NFS Configuration:

   - **Server Configuration [masterpi]**

     ``# sudo mkdir /cluster_shared``
   
     > Add the "cluster_shared" directory to NFS.
        
       ``# sudo vim /etc/exports``

         > Add the following line to the end of the file:
            
         ``\/cluster_shared     *(rw,sync)``
   
     ``# sudo chown -R nobody.nobody /cluster_shared``
   
     > Edit the "nfs-common.conf" file.
        
       ``# sudo vim /etc/conf.d/nfs-common.conf``

         > Find "STATD_OPTS=". Change it to:
            
         ``STATD_OPTS="-no-notify"``

   - **Client Configuration [slavepiX]**
   
     > Add the "cluster_shared" NFS share to the client.
     
       ``# sudo vim /etc/fstab``
       
         > Add the following line to the end of the file:
       
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
