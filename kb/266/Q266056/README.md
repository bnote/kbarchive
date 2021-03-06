---
layout: page
title: "Q266056: Error Message Appears Stating that Video Drivers Not Installed"
permalink: /kb/266/Q266056/
---

## Q266056: Error Message Appears Stating that Video Drivers Not Installed

{% raw %}

	Article: Q266056
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are performing an upgrade from Windows NT Workstation 3.51 to Windows
	NT Workstation 4.0 on a Hewlett-Packard Vectra computer with an S3 video card
	installed, and you manually try to change the video settings, you may receive
	the following error messages:
	
	  The drivers were not installed successfully
	
	  You may not have required privileges to install drivers
	
	When you check the VgaStart, the VgaSave, and the S3 keys in the registry, you
	find that the correct permissions are set.
	
	CAUSE
	=====
	
	This behavior can occur because of registry corruption.
	
	RESOLUTION
	==========
	
	To resolve this behavior, install a parallel copy of Windows NT Workstation 4.0
	and boot to the parallel installation. Use the Registry Editor to edit the
	system hive of the original installation to boot to VGA. Boot to the original
	installation, and reinstall the video drivers.
	
	MORE INFORMATION
	================
	
	IMPORTANT: This article contains information about modifying the registry.
	Before you modify the registry, make sure to back it up and make sure that you
	understand how to restore the registry if a problem occurs. For information
	about how to back up, restore, and edit the registry, click the following
	article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To make the necessary changes, follow these steps:
	
	1. Install a parallel installation of Windows NT Workstation 4.0.
	
	2. Restart the computer to the parallel installation.
	
	3. Copy the Vga.dll file from the %SystemRoot%\System32 folder of the parallel
	  installation to the same folder of the original installation.
	
	4. Edit the registry to configure the original installation to start in VGA
	  mode:
	
	  a. From the parallel installation, use Registry Editor (Regedt32) to load the
	     system hive of the original installation:
	
	     1. From the HKEY_LOCAL_MACHINE hive, click HKEY_LOCAL_MACHINE. Select the
	        Registry menu, and then click Load Hive.
	
	     2. Browse to the %SystemRoot%\System32\Config\ folder of the original
	        installation, click System, and then click Open.
	
	     3. In the Key Name box, type "Test" (without the quotation marks), and
	        then click OK.
	
	  b. Edit the original system hive:
	
	     1. Use Registry Editor to locate the following registry key:
	
	        HKEY_LOCAL_MACHINE\TEST\ControlSetXXX\Services\VgaSave
	
	        (where XXX represents the control set number that your computer should
	        start from the next time you restart it).
	
	        NOTE: The number of the control set you need to locate is determined by
	        the registry value Current in the following registry location:
	
	        HKEY_LOCAL_MACHINE\SYSTEM\Select
	
	     2. Make sure the value data for the ImagePath value reads:
	
	        SystemRoot\System32\Drivers\Vga.sys
	
	     3. Locate the following registry key:
	
	        HKEY_LOCAL_MACHINE\TEST\ControlSetXXX\Services\VgaSave\Device0
	
	     4. In the right pane of the Registry Editor window, double-click the value
	        InstalledDisplayDrivers. Change the value data to VGA, and then click
	        OK.
	
	  c. Unload the system hive of the original installation to save the changes:
	
	     1. Collapse the HKEY_LOCAL_MACHINE\TEST key. Make sure it is highlighted.
	
	     2. On the Registry menu, click Unload Hive, and then click Yes to confirm
	        the command.
	
	5. Restart the computer in VGA mode to the original installation.
	
	6. Reinstall the driver for your video adapter.
	
	7. Perform the preceding steps also for the following registry keys:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\ControlSetXXX\Services\S3
	
	  HKEY_LOCAL_MACHINE\SYSTEM\ControlSetXXX\Services\VgaStart
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
