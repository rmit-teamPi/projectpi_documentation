Arch Linux Arm
--------------

- Resizing:
	# fdisk /dev/mmcblk0
	>> p
	>> d
	>> 2
	>> n
	>> e
	>> (return) # accept default partition no
	>> (return) # accept default start
	>> (return) # accept default end
	>> n
	>> l
	>> (return) # accept default start
	>> (return) # accept default end
	>> p
	>> w

	# sync; reboot 
	...
	# resize2fs /dev/mmcblk0p5

- Set the hostname:
	# echo > /etc/hostname

- WiFi:
	**To Connect:**
	# wifi-menu -o

	--> Pick network to connect.

	**To Auto Connect:**
	# netctl list
	# cp /etc/netctl/wlan0-*** /etc/netctl/<profile>
	# netctl start <profile>
	# netctl enable <profile>

- Update System:
	# pacman-key --init

	In a different console (Alt+F2):
	# ls -R / && ls -R / && ls -R /

	Check first console for key init finished.
	# pacman -Syu

- Users and Groups:
	# useradd -m <username>
	# passwd <username>

	# groupadd admin
	# gpasswd -a <username> admin

- Install:
	1) Sudo:
		- Give "admin" group sudo rights.
			# visudo

			Find "#%wheel ALL=(ALL) ALL". Add the line:
			%admin ALL=(ALL) ALL
	2) Vim
	3) Git
	4) Python 2
		# pacman -S python2
	5) GCC
		# pacman -S gcc
	6) OpenMPI
		# pacman -Syy openmpi

