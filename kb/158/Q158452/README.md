---
layout: page
title: "Q158452: How to Configure Windows 95 Remoteboot on Windows NT 4.0"
permalink: /kb/158/Q158452/
---

## Q158452: How to Configure Windows 95 Remoteboot on Windows NT 4.0

{% raw %}

	Article: Q158452
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article explains the steps required to install and configure Windows 95 for
	the Remoteboot service under Windows NT Server 4.0. Prior to performing any of
	the steps outlined in this article, you must have properly installed the
	Remoteboot service on Windows NT and have configured the remoteboot client for
	MS-DOS. For more information, please see the following articles here in the
	Microsoft Knowledge Base:
	
	  Article-ID: Q158277
	  TITLE : How to Configure DOS for Remoteboot on Windows NT 4.0
	
	  Article-ID: Q158454
	  TITLE : How to Install Remoteboot on Windows NT 4.0
	
	For this article, it is assumed that your system's Remoteboot service,
	Server-Based Setup (SBS) installation directory, and machine directory reside in
	a Windows NT 4.0 Server configured for remoteboot.
	
	MORE INFORMATION
	================
	
	Requirements
	------------
	
	An SBS of Windows 95 requires 90 megabytes (MB) of available disk space on the
	server, as well as an additional 2 MB for the Windows 95 client configuration
	files and at least 10 MB for each Windows 95 machine directory. More disk space
	is required if users install additional software.
	
	The remoteboot client computer requires 8 MB of RAM, must use a 386DX or higher
	processor, and must have a supported Remoteboot Network Card.
	
	Installing SBS for Windows 95 Clients
	-------------------------------------
	
	The following procedures are taken from the Windows NT Server Networking Guide
	Help file in the Windows NT 4.0 Resource Kit.
	
	For more information about SBS servers, see the Microsoft Windows 95 Resource
	Kit. The resource kit describes additional purposes, beyond remoteboot, that you
	can use an SBS server for.
	
	To install an SBS server for a Windows 95 client, you will need a Windows 95
	installation compact disc (not to be confused with a floppy disk) and the
	Windows 95 client computer. You must then complete the following steps:
	
	1. On the server that will contain the SBS files, create a shared directory with
	  90 MB of available disk space. The shared directory can have any name.
	
	  NOTE: As you share the directory, assign read-only permission for regular
	  users and full access for administrators. Use Server Manager to focus on the
	  shared directory, and set read-only permission for the Users group and full
	  permission for the Administrators group. In File Manager, on the Disk menu,
	  click Share As (do NOT open the Security menu and click Permissions).
	
	2. Install one regular Windows 95 client on the network or use an existing one.
	  You will use this client to configure the SBS server.
	
	3. Log on to the Windows 95 client using an account that has write access to the
	  shared directory on the SBS server.
	
	4. Put the Windows 95 compact disc in the client's CD-ROM drive. In Windows
	  Explorer, switch to the Admin\Nettools\Netsetup directory.
	
	  NOTE: Only the retail version of Windows 95 includes the Netsetup.exe utility.
	  Windows 95 OEM Service Release 1, 2, and 2.5 do not include the Netsetup.exe
	  utility.
	
	5. Double-click the file Netsetup.exe.
	
	  Note that you must run Netsetup.exe at a Windows 95 client. Errors will occur
	  if you run this file on a computer running Windows NT.
	
	6. In the Server-Based Setup dialog box, click Set Path, and specify the path to
	  the SBS server. In specifying the path, you can type a drive letter for a
	  mapped drive, a network name for a server (for example, \\server1\sharedir),
	  or a network path to a specific directory (for example,
	  \\server1\sharedir\rpl\win95). The button name becomes Change Path if a
	  server was defined previously.
	
	7. Click OK, then click Install.
	
	8. Server-Based Setup now presents you with a series of dialog boxes asking you
	  to select among various options. The boxes you see may include the following:
	
	   - A dialog box for specifying an installation policy controlling how users
	     can install Windows 95 from the server. If you support only remoteboot
	     clients, click Server. If you support other SBS functions as well, click
	     User's Choice. Do not click Local Hard Drive.
	
	   - A dialog box for setting the source path for Windows 95 files. This is the
	     path to the compact disc on the client.
	
	   - A dialog box for indicating whether you want to create a default setup
	     script. Specify that you do NOT want to create a default setup script.
	     Setup scripts for Windows NT remoteboot installation require special
	     settings.
	
	   - A dialog box for providing a CD Key number for product identification.
	
	   - A dialog box for directing Server-Based Setup to copy Windows 95 files to
	     the SBS shared directory.
	
	9. At the remoteboot server, insert the compact disc or floppy disk containing
	  the Windows NT remoteboot for Windows 95 files. Change to the newly inserted
	  disc or disk, then change to the Update\Win95 directory. To update the
	  Windows 95 files for remotebooting, run Win95srv.bat. The following inputs
	  illustrate this process:
	
	     d:
	     cd \clients\rpl\update\win95
	     win95srv.bat <dest>
	
	  where <dest> is the shared directory on the SBS server.
	
	10. If you are updating from version 3.51 or earlier of the Remoteboot service,
	  start the Remoteboot service at the remoteboot server (if it is not already
	  started). Then run the program Rbootsrv.bat to update the remoteboot files
	  and database for Windows 95 remotebooting. Thus, at the server's command
	  prompt, you would type:
	
	  d:
	  cd \clients\rpl\update\win95
	  rbootsrv.bat <SBS_path> <RPL_path> [\\servername]
	
	  where:
	
	   - <SBS_path> is the path to the installed SBS server's Windows 95
	     files.
	
	   - <RPL_path> is the path to the remoteboot directory.
	
	   - \\servername is the name of the remoteboot server (you can omit this if
	     you are typing at the remoteboot server).
	
	11. At the remoteboot server, start Remoteboot Manager.
	
	12. On the Configure menu, click Check Configurations to activate the new
	  configurations.
	
	Installing the First Windows 95 Client
	--------------------------------------
	
	Each remoteboot client has a machine directory. This directory contains
	client-specific configuration information and data. Stored here are the
	appropriate initialization and configuration files, the registry, desktop, start
	menu directories, spool directories and the swap file and temp directories.
	These machine directories can reside on any server on the network provided that
	the server is running NetBEUI and IPX protocols and that there is ample disk
	space available. You may want to spread the load of the machine directories
	across servers.
	
	1. On the server that will contain the machine directory, create a shared
	  directory with at least 10 MB of space available per client. Additional space
	  may be needed depending on the installed applications. The share directory
	  can have any name and be located in any directory. One suggestion is that you
	  create the directory under the WINNT\RPL and supply a name of Win95.mac.
	
	  NOTE: The server for the machine directory must be in the same domain or
	  workgroup as the SBS server.
	
	  NOTE: The machine directories may not be subdirectories of the SBS directory.
	
	2. Set the permissions for the share and directory (NTFS only). The group
	  RPLUSERS and the group ADMINISTRATORS both need full control.
	
	  NOTE: For added security (NTFS only), assign the permissions to a machine
	  directory so that only the users who will use the client have full control of
	  the machine directory for that remoteboot computer.
	
	3. Boot the remoteboot client with DOS 6.2x.
	
	4. Using the NET LOGON command, log on to the remoteboot client using an account
	  that has read access to the SBS server and write access to the server with
	  the machine directory share. Many users have found it easier to use the
	  administrator account during the installation process for full access to all
	  systems.
	
	5. Using the NET USE command, map one drive to the SBS share and another to the
	  machine directory share.
	
	  NOTE: The drive letters used during this step cannot be changed and will be
	  dedicated to the booting and operation of the Windows 95 remoteboot client.
	  For example, in the following:
	
	  net use F: \\NTSERVER\WIN95.SBS
	  net use G: \\NTSERVER\WIN95.MAC
	
	  drive F is mapped to the Windows 95 SBS and drive G is mapped to the Windows
	  95 machine directory share. These drive letters cannot be changed or used for
	  other shares since Windows 95 uses them during its operation.
	
	6. Change to the drive letter mapped to the SBS share. In the above example,
	  this is drive F.
	
	7. Run the Windows 95 Setup program by typing:
	
	  Setup /t:temppath
	
	  where /t: is required and temppath is a path to a directory to store temporary
	  files during the installation. This path could be G:\win.tmp. Note that the
	  temp path is completely removed after completing the installation of Windows
	  95.
	
	  NOTE: You may want to use SETUP /T:TEMPPATH /IW /IS MSBATCH.INF. This bypasses
	  licensing during setup and skips scandisk.
	
	8. Setup will display the following dialog boxes:
	
	   - Server-Based Setup dialog box. Select "Setup Windows to run from a network
	     server."
	
	   - Startup Method dialog box. Select "Start Windows from the network
	     (remoteboot server)."
	
	   - Machine Directory dialog box. Enter the drive letter and a directory to
	     install the Windows 95. (The drive letter must be the same drive letter
	     mapped for the computer's directory, and the directory name should reflect
	     the configuration for the computer. For example, G:\DELL5166 might be used
	     for a Dell Pentium 166. The directory is created during setup.)
	
	   - Setup Options dialog box. Choose custom setup.
	
	   - Analyzing Your Computer dialog box. Select "No, I want to modify the
	     hardware list." (You should exclude as many hardware types and items from
	     the auto-detection as possible. If during the auto-detection phase, the
	     system fails, you should restart the setup process and exclude more items
	     from the auto-detection phase.)
	
	     NOTE: If your network adapter is using IRQ2 or IRQ3, this will conflict
	     with the serial port detection and possibly cause the system to fail
	     during Setup.
	
	   - Select Components dialog box. Clear the checkbox for Communications if
	     your remoteboot client doesn't have a modem.
	
	   - Network Configuration dialog box. Select the appropriate network adapter
	     and the desired protocols. If your network adapter is not displayed, you
	     will have to add and configure your adapter.
	
	     NOTE: If you add your network adapter, you must confirm the resource
	     settings for the adapter by selecting OK. If you select Cancel, your
	     Windows 95 remoteboot setup will fail to boot properly.
	
	   - Identification dialog box. Make sure the workgroup name is the same as the
	     domain or workgroup name of the SBS server and machine directory server.
	
	When the Windows 95 setup program completes, reboot the client and either turn it
	off or leave it at the prompt that asks you whether you want to boot from the
	network or not.
	
	9. At the remoteboot server, start the Remoteboot Manager.
	
	10. Create a profile for the Windows 95 client. In the Configuration box, choose
	  the Windows 95 configuration that corresponds to the client's network
	  adapter type. The adapter type should be the same one used to do the DOS6.2x
	  remoteboot.
	
	11. Select the client's workstation record by double-clicking on it or selecting
	  Properties from the Remoteboot menu, and assign the new Windows 95 profile.
	
	12. Once the profile has been configured, you need to move the client- specific
	  Windows 95 real-mode boot files from the client's machine directory to the
	  Rpl\Rplfiles\ Profiles\<profile_name> directory on the remoteboot
	  server. To do this, go to the remoteboot server (or a client with write
	  access to the remoteboot server's Rpl directory), and run the
	  Rpl\Bin\Win95clt.bat program by typing:
	
	  cd <systemroot>\rpl\bin
	  win95clt mach_directory \\rpl_server profile_name
	
	  where:
	
	   - mach_directory is the path to the client's machine directory.
	
	   - \\rpl_server is the name of the remoteboot server.
	
	   - profile_name is the name of the Windows 95 profile associated with the
	     client.
	
	  For example, you could type:
	
	  cd \winnt\rpl\bin
	  WIN95CLT G:\DELL5166 \\NTSERVER WIN95
	
	  NOTE: You must have a drive letter explicitly pointing to the machine
	  directory and cannot specify the UNC name for the location of the machine
	  directory. If you try to use the UNC name, the remoteboot client will not be
	  able to locate the full registry during the boot process.
	
	  NOTE: If the machine directory is on the same computer as the Remoteboot
	  service, then you can just type in the local path.
	
	13. At the SBS server, edit the Machines.ini file in the SBS directory. Add the
	  following lines for the new client.
	
	     [Adapter ID]
	     SysDatPath=G:\machine_dir
	     G=\\mach_server\mach_share
	
	  where:
	
	   - Adapter ID is the network adapter ID (MAC address from manufacturer)
	     specified in the remoteboot workstation record for this client.
	
	   - G:\machine_dir is the location of the client's machine directory on a
	     server.
	
	  NOTE: The drive letter G: is the same drive letter assigned during the
	  installation of Windows 95 for the machine directory.
	  G=\\mach_server\mach_share assigns a drive letter to the shared directory
	  where the machine directory resides. The G= should be the same drive letter
	  assigned during the installation of the Windows 95 for the machine
	  directory.
	
	  Based on our previous examples, the Machine.ini for our client would contain
	  the following:
	
	        [12345AB67C89]
	        SYSDATPATH=G:\DELL5166
	        G=\\NTSERVER\WIN95.MAC
	
	14. Power on the remoteboot client. The client will now boot to Windows 95 and
	  complete the Windows 95 Setup program.
	
	For more information about installation, refer to the Windows NT 4.0 Resource
	Kit.
	
	Additional query words: nt rpl remote boot win95 sbs remoteboot
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : 4.0
	
	=============================================================================
	

{% endraw %}
