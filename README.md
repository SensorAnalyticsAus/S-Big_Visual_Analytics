About
=====
S-BigVA™ is a fully functional *visual analytics* application implemented within a VirtualBox virtual machine (VM). It can be used for finding anomalies (unique events) within videos and image repositories.

Demo Videos
===========
[HTHH]: https://youtu.be/YRoUk5oB1qo
[SITS]: https://youtu.be/Kfcy5US43cI
- House on Haunted Hill (1959) an A.I. Rendition [HTHH]
- Swallows in the Sun [SITS]

Background Knowledge
====================
Users with some prior experience in using a virtual machine and ssh will find using the app quite easy and may even be able to further customise it to fit into their own work flow e.g. home security cameras ftp'ing motion detected videos or snaps to the VM for daily video content analysis and alerts say with cron.

System Requirement
==================
- 16GB memory (8GB for the PC host itself and 8GB for this VM)
- 71GB free disk space [max]
- Oracle VirtualBox version 6.1 or higher
- OS: MacOS (Intel), Win10 or above, Linux (in short any OS capable of running VirtualBox)

Installation
============
[Downloaded from here]: https://www.sensoranalytics.com.au/assets/html/va-download.html
- S-BigVA VM can be [Downloaded from here]. The VM's login and samba login are both the same. Username: saauser password: saauserV7 
- Double clicking on the downloaded bigva*.ova distro file will import the VM into VirtualBox, process may take several minutes to few hours depending on the cpu-speed of the host PC. 
- Adjust memory according to the host PC from the VM Settings (System menu). Allocate 4GB to this VM for an 8GB memory computer.
- Once import is completed, pressing the start button will launch the VM (errors and warnings can be safely ignored as long as the VM continues its boot-up).
- During VM startup, please allow VirtualBox to open required port in the PC's firewall if prompted.
- During VM startup, if a dialog box appears regarding a network interface not being present, please select the [network interface setting] option and select the interface that's available on your system.

Use
===
- The VA-app is designed to be used from host PC. Normally login to VM is not needed. The app can be launched in a web browser as http://localhost:8081 
- Opening a web browser on PC host http://localhost:8081 or its IP Address (as shown in login screen) will bring up the VA-app. Web Login shell, for accessing the VM for admin etc, is at https://localhost:12320 or https://router_assigned_ip:12320 (note it uses https hence browser exception has to be added when prompted).

- Follow within-app instructions to start analysing videos or image folders for discovering anomalous (strange) events.

- VM's and host PC's ip addresses are in the pre and post login splash screens, may need to scroll back to see. These can also be found by executing ifconfig -a in the ssh/web shell. There are three options to exchange data with the VA-app:

	(1) Once VM's ip address is known, files can be transferred from host PC --> VM using scp (or putty for win). NB: for scp and ssh the address should be saauser@your_router_assigned_ip instead of root@... as shown in the blue startup screen (we can only use root@... after root password is chosen).
	(2) VM also exports its ~/upload folder as a samba share, which can also be used for data transfers.
Instructions for accessing VM folder on Win10 PC: https://www.techrepublic.com/article/how-to-connect-to-linux-samba-shares-from-windows-10/
	(3) Installing VirtualBox Guest Addition and enabling the shared folder(s) between the VM and the host PC.


Getting Started Example
=======================
Please click the 00-va-App 0.2.x link showing on the Zeppelin Home page. Several image folders are provided within the VM at /home/saauser/upload for testing. 

The VA-App loads one such example on startup. User inputs are already pre-filled in the 'Load Frames', 'KMeans', 'Select a Cluster', and 'Scene Inspector' paragraphs. This notebook should be initially run by clicking the run-all triangle button at the top. 

NB: For repeat trials with varying number of clusters, only the 'KMeans' and the two subsequent paragraphs need to be run (from paragraph's cog-wheel 'Run all below' option), [for further information].
							
[for further information]: https://sensoranalytics.com.au/#_va

Troubleshooting
===============
- VM window appears too small or too large. Size can be adjusted from View->Virtual Screen sub-menu of VirtualBox to suit the PC's display.
- Zeppelin keeps failing, increase VM memory. Useful Zeppelin admin commands:
	- zeppelin-daemon status/stop/start/restart
- iPython errors, reduce number of images in the jpg folder or increase VM memory.
- URL fails to load, please make sure no other program on your PC is using port 8081 or PC's firewall is not blocking this port. If so,  Zeppelin port can be changed from VM's Network Settings, NAT, Advanced, and changing 'host port' from 8081 to say 8082. NB: this fix will only work for http://localhost:[new_port_no] URL.
- 'KMeans' pie chart is not showing. May need to drag the tiny triangle in bottom-right of the chart area down to expose the pie chart. This will happen with 100s of clusters, where the index takes too much space out of the default display area for the chart. 



© 2022 https://www.sensoranalytics.com.au/
