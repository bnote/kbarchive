---
layout: page
title: "Q155648: Cannot Connect To MSN At Maximum Modem Speed"
permalink: /kb/155/Q155648/
---

## Q155648: Cannot Connect To MSN At Maximum Modem Speed

{% raw %}

	Article: Q155648
	Product(s): The Microsoft Network
	Version(s): 2.6,5.0,5.1,5.2,5.4
	Operating System(s): 
	Keyword(s): kbenvkbfaq
	Last Modified: 17-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network versions 2.6, 5.0, 5.1, 5.2, 5.4 
	- The Microsoft Network Version 5.6 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Although you have previously connected to MSN, The Microsoft Network, at your
	modem's maximum speed, you are now unable to connect at this speed.
	
	CAUSE
	=====
	
	This issue can occur because:
	
	- The MSN Dial-Up Networking connection may be damaged.
	
	- The modem may not be configured for optimum performance
	
	- Phone line conditions may have changed.
	
	- Network congestion may be greater due to higher traffic or problems with
	  connections or cables somewhere on the network.
	
	RESOLUTION
	==========
	
	To resolve this issue, use any of the following methods:
	
	Delete MSN Dial-Up Networking Connections
	-----------------------------------------
	
	To delete the two MSN Dial-Up Networking connections, follow these steps:
	
	1. Double-click My Computer, and then double-click Dial-Up Networking.
	
	2. Delete any connections named MSN, The Microsoft Network or The Microsoft
	  Network (Backup).
	
	3. Right-click the MSN desktop icon, and then click Connection Settings.
	
	4. Click Access Numbers, and then reselect both the primary and backup telephone
	  numbers.
	  -or-
	  In later versions the numbers will be stored and you only need to double-click
	  the desktop icon to recreate the dialer.
	
	Optimize Modem Performance
	--------------------------
	
	To configure your modem for optimum performance in Windows 95/98, follow these
	steps:
	
	NOTE: Using these steps does not guarantee that a 28.8 modem will always transfer
	data at a rate of 28.8 Kbps or higher. These are simply steps you can use to
	configure your modem for optimum performance in Windows 95/98.
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Modems.
	
	3. On the General tab, click the modem you are using to connect to MSN, and then
	  click Properties.
	
	4. In the Maximum Speed box, click 57600.
	
	  NOTE: Do not set the maximum connection speed higher than 57600 Kbps if you
	  are using a 28.8 Kbps modem. A 56k Modem should be set to 115200
	
	5. Click the Only Connect At This Speed check box to clear it.
	
	6. On the Connection tab, click Advanced.
	
	7. Click the Use Flow Control check box to select it, and then click Hardware
	  (RTS/CTS).
	
	8. Click the Use Error Control check box to select it.
	
	9. Click OK, click OK again, and then click Close.
	
	MORE INFORMATION
	================
	
	You can use the Modemlog.txt file located in the Windows folder to troubleshoot
	modem connection problems. To enable the Modemlog.txt file, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Modems.
	
	3. On the Connection tab, click Advanced.
	
	4. Click the Record A Log File check box to select it.
	
	5. Click OK, click OK again, and then click Close.
	
	For information about interpreting the contents of the Modemlog.txt file, see the
	following article in the Microsoft Knowledge Base:
	
	  Q142730 How to Create and Use the Modemlog.txt File
	
	Additional information
	----------------------
	
	Telephone line quality should be taken into consideration if there is a dramatic
	decrease in connection speeds. If you notice this change after changing dialing
	locations (i.e. moving to another location) or after a thunderstorm or
	electrical storm, you may need to consult the local telephone company to check
	for excess line noise or damage to the telephone lines and phone equipment.
	Damage to the lines and excess static in the lines can cause a lower connection
	speed.
	
	Additional query words: msn kbimu
	
	======================================================================
	Keywords          : kbenv kbfaq
	Technology        : kbMSNSearch kbMSN520 kbMSN510 kbMSN500 kbMSN260 kbMSN560 kbMSN540
	Version           : :2.6,5.0,5.1,5.2,5.4
	Issue type        : kbprb kbinfo
	
	=============================================================================
	

{% endraw %}
