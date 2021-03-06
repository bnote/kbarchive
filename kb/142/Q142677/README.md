---
layout: page
title: "Q142677: Base Priority of the CMD Process"
permalink: /kb/142/Q142677/
---

## Q142677: Base Priority of the CMD Process

{% raw %}

	Article: Q142677
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbother
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Under Windows NT 4.0 Workstation or Server, the base priority of the command
	(CMD) process and of the thread that runs in it is set to 8 by default.
	
	MORE INFORMATION
	================
	
	Under Windows NT 3.x, the base priority of the CMD process and the thread that
	runs in it used to be set to 7; the system could boost the thread from priority
	7 to priority 9.
	
	As previously stated, under Windows NT 4.0 the base priority of the CMD process
	and the thread that runs it is now set to 8 by default. The system can still
	boost the thread priority by 2 points, but now the increase is from priority 8
	to priority 10.
	
	To check this change, simply start a CMD process and start Performance Monitor.
	Check the chart with Object: Process and Counter: Priority Base for the
	Instance: CMD.
	
	You can also check the chart with Object: Thread and Counter: Priority Base vs.
	Counter: Priority Current for the Instance: CMD.
	
	Additional query words: prodnt
	======================================================================
	Keywords          : kbother 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : 4.0
	
	=============================================================================
	

{% endraw %}
