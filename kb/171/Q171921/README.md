---
layout: page
title: "Q171921: Error Message: Error Loading Nwserver - Error 6260"
permalink: /kb/171/Q171921/
---

## Q171921: Error Message: Error Loading Nwserver - Error 6260

{% raw %}

	Article: Q171921
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95
	Operating System(s): 
	Keyword(s): kberrmsg kbnetwork win95
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, you should first make a backup copy of the
	registry files (System.dat and User.dat). Both are hidden files in the
	Windows folder.
	
	SYMPTOMS
	========
	
	When you start Windows, you may receive an error message similar to the
	following message:
	
	  The following error occurred while loading the device NWServer Error 6260: No
	  Workgroup has been specified. To specify one, double-click the network icon
	  in control panel, and then click the identification tab.
	
	CAUSE
	=====
	
	This behavior may be caused by one of the following situations:
	
	- The Nwserver.vxd file is missing or damaged.
	
	- The registry was not updated correctly when the Client for NetWare Networks
	  component or the "File and printer sharing for NetWare Networks" component
	  was removed.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following methods:
	
	Method 1
	--------
	
	If you connect to a NetWare server, add the "File and printer sharing for NetWare
	Networks" component. To do so, follow these steps:
	
	1. In Control Panel, double-click the Network icon.
	
	2. Click Add, click Service, and then click Add.
	
	3. In the Manufacturers box, click Microsoft. In the Network Services box, click
	  "File and printer sharing for NetWare Networks," and then click OK.
	
	4. Click OK.
	
	5. Restart your computer when you are prompted to do so.
	
	NOTE: File and printer sharing for NetWare networks cannot be installed together
	with file and printer sharing for Microsoft networks.
	
	Method 2
	--------
	
	If you do not connect to a NetWare server and the "File and printer sharing for
	NetWare Networks" component is not installed, add and then remove the "File and
	printer sharing for NetWare Networks" component. To do so, follow these steps:
	
	1. In Control Panel, double-click the Network icon.
	
	2. Click Add, click Service, and then click Add.
	
	3. In the Manufacturers box, click Microsoft. In the Network Services box, click
	  "File and printer sharing for NetWare Networks," and then click OK.
	
	4. Click OK.
	
	5. Restart your computer when you are prompted to do so.
	
	6. In Control Panel, double-click the Network icon.
	
	7. Click "File and printer sharing for NetWare Networks", and then click Remove.
	
	8. Click OK.
	
	9. Restart your computer when you are prompted to do so.
	
	Method 3
	--------
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall Windows 95. Microsoft cannot guarantee that problems
	resulting from the incorrect use of Registry Editor can be solved. Use Registry
	Editor at your own risk.
	
	NOTE: For information about how to edit the registry, view the Changing Keys And
	Values online Help topic in Registry Editor (Regedit.exe). Note that you should
	make a backup copy of the registry files (System.dat and User.dat) before you
	edit the registry.
	
	The steps listed above should resolve the issue. If the error message persists,
	use Registry Editor to delete the StaticVxD value in the NWServer subkey under
	the following registry entry:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\VxD\NWServer
	
	Additionally, you may need to remove the following key:
	
	  HLM\System\CurrentControlSet\PerfStats\Enum\NWServer
	
	MORE INFORMATION
	================
	
	When you add the "File and printer sharing for NetWare Networks" component, the
	Nwserver.vxd file is copied to your hard disk. If you cancel the installation,
	or when sharing is changed to "File and printer sharing for Microsoft Networks,"
	the registry keys that reference the Nwserver.vxd file may not be removed.
	
	======================================================================
	Keywords          : kberrmsg kbnetwork win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : WINDOWS:95
	
	=============================================================================
	

{% endraw %}
