---
layout: page
title: "Q236963: Creating Hardware Profiles for Windows 95/98 and Windows NT 4.0"
permalink: /kb/236/Q236963/
---

## Q236963: Creating Hardware Profiles for Windows 95/98 and Windows NT 4.0

{% raw %}

	Article: Q236963
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95; winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 98 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you troubleshoot or configure clients and servers, it is often necessary to
	create a hardware profile. This article describes how to create hardware
	profiles for Windows 95, Windows 98, and Windows NT 4.0.
	
	MORE INFORMATION
	================
	
	For Windows 95
	--------------
	
	1. Right-click My Computer, and then click Properties.
	
	2. On the Hardware Profiles tab, click the Original Configuration profile, and
	  then click Copy.
	
	3. You are prompted to type a name for the copied profile. Type a name that
	  easily identifies the profile (for example, Network Disabled), and then click
	  OK.
	
	4. After you create the profile, you must configure your devices for that
	  profile. Restart your computer and choose the hardware profile that you want
	  to edit. In this example, click the Network Disabled hardware profile. After
	  you choose the hardware profile, you are logged in normally.
	
	5. Right-click My Computer, and then click the Device Manager tab.
	
	6. On the Device Manager tab, you can select a hardware component. In this
	  example, click to select a network adapter, and then click Properties.
	
	7. A dialog box is displayed, and you can choose one of the following options:
	
	   - Disable in this hardware profile
	
	   - Remove from this hardware profile
	
	NOTE: When you choose either of these options, the hardware is unusable when
	Windows 95 is started into this profile.
	
	For Windows 98
	--------------
	
	1. Right-click My Computer, and then click Properties.
	
	2. On the Hardware Profiles tab, click the Original Configuration profile, and
	  then click Copy.
	
	3. You are prompted to type a name for the copied profile. Type a name that
	  easily identifies the profile (for example, Network Disabled), and then click
	  OK.
	
	4. After you create the profile, you must configure your devices for that
	  profile. Restart your computer and choose the hardware profile that you want
	  to edit. In this example, click the Network Disabled hardware profile. After
	  you choose the hardware profile, you are logged in normally.
	
	5. Right-click My Computer, and the click the Device Manager tab.
	
	6. On the Device Manager tab, you can select a hardware component. In this
	  example, click to select a network adapter, and then click Properties.
	
	7. A dialog box is displayed, and you can choose one of the following options:
	
	   - Disable in this hardware profile
	
	   - Exists in all hardware profiles
	
	NOTE: In Windows 98, the second option is always selected for network adapters.
	To delete the network adapter from this hardware profile, clear the "Exists in
	all hardware profiles" option, and then click to select the "Disable in this
	hardware profile" option. This action renders the network adapter unusable when
	Windows 98 is started into this profile.
	
	For Windows NT 4.0
	------------------
	
	1. Right-click My Computer, and then click Properties.
	
	2. On the Hardware Profiles tab, click the Original Configuration (Current)
	  profile, and then click Copy.
	
	3. You are prompted to type a name for the copied profile. Type a name that
	  easily identifies the profile (for example, Network Disabled), and then click
	  OK.
	
	4. After you create a new profile, you can use the following methods to disable
	  devices and services:
	
	   - Disable a Device
	
	     a. In Control Panel, double-click Devices.
	
	     b. Click any device in the list, and then click HW Profiles.
	
	     c. A dialog box is displayed, showing each hardware profile and the status
	        of the selected device in each of these profiles. Initially, all
	        devices are enabled for all hardware profiles. To disable a device,
	        simply select the appropriate hardware profile, and then click Disable.
	
	   - Disable a Service
	
	     a. In Control Panel, double-click Services.
	
	     b. Click any service in the list, and then click HW Profiles.
	
	     c. A dialog box is displayed, showing each hardware profile and the status
	        of the selected service in each of those profiles. Initially, all
	        services are enabled for all hardware profiles. To disable a service,
	        simply select the appropriate hardware profile, and then click Disable.
	
	NOTE: If you want to create a "no-network" profile, the steps outlined above are
	unnecessary. Windows NT 4.0 is designed so that laptops and client computers can
	be started with no network configuration. To take advantage of this feature,
	create a hardware profile and name it "No Network," or something equally
	informative.
	
	After you create this profile (using the steps outlined above for Windows NT
	4.0), click the profile, and then click Properties. A dialog box is displayed.
	On the General tab, you can determine whether this computer is a laptop or not
	and what state the computer is in with this profile. On the Network tab, you can
	click to select the Network-disabled hardware profile check box. When you choose
	this option, all network adapters in this profile are disabled.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400xsearch kbWinNTSsearch kbWinNTS400xsearch kbWinNTS400 kbWin95search kbWin98search kbZNotKeyword3 kbWin98
	Version           : WINDOWS:95; winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
