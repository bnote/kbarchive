---
layout: page
title: "Q216783: Unable to Completely Disconnect a Terminal Server Connection"
permalink: /kb/216/Q216783/
---

## Q216783: Unable to Completely Disconnect a Terminal Server Connection

{% raw %}

	Article: Q216783
	Product(s): Microsoft Windows NT
	Version(s): 2000,4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbtool kbui
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows 2000 Server 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	After a Terminal Server client loses the connection to a Terminal Server, the
	session on the Terminal Server may not transition to a disconnected state,
	instead, it may remain active even though the client is physically disconnected
	from the Terminal Server. If the client logs back in to the same Terminal
	Server, a totally new session may be established, and the original session may
	still remain active.
	
	CAUSE
	=====
	
	This issue can occur because Terminal Server implements a Keep Alive mechanism.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	For Windows NT 4.0 Terminal Server Edition
	------------------------------------------
	
	To work around this issue:
	
	1. Apply the latest service pack for Windows NT 4.0, Terminal Server Edition.
	
	2. Use Registry Editor to add a DWORD value, "KeepAliveEnable" (without the
	  quotation marks), with a Positive numeric value of 1 (which represents 1
	  minute) to the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server
	
	3. In the "Terminal Server Connection Configuration" tool, double-click rdp-tcp,
	  and then click Advanced.
	
	4. On the "On a broken or timed-out connection, <connect action> the
	  session" line, click to clear the inherit user config option. Click
	  Disconnect on "On a broken or timed-out connection, <connect action>
	  the session", and then click OK.
	
	For Windows 2000 Terminal Server
	--------------------------------
	
	1. Use Registry Editor to add a DWORD value, "KeepAliveEnable" (without the
	  quotation marks), with a positive numeric value of 1 (which represents 1
	  minute) to the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server
	
	2. Open "Terminal Services Configuration" in Administrative Tools, double-click
	  RDP-Tcp in the Connections folder and click the Sessions tab.
	
	3. Click to select "Override user settings" and make sure that "Disconnect from
	  session" is selected and then click OK.
	
	
	Additional query words: terminalsvr
	
	======================================================================
	Keywords          : kbnetwork kbtool kbui 
	Technology        : kbWinNTsearch kbWinNT400search kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbwin2000ServSearch kbwin2000Search kbNTTermServ400 kbNTTermServSearch
	Version           : :2000,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
