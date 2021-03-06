---
layout: page
title: "Q101932: PC Win: Expansion of Groups, Revealing Group Members"
permalink: /kb/101/Q101932/
---

## Q101932: PC Win: Expansion of Groups, Revealing Group Members

{% raw %}

	Article: Q101932
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:2.1d,3.0,3.0b,3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for Windows, versions 2.1d, 3.0, 3.0b, 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you use version 2.1d, 3.0, 3.0b, or 3.2 of Microsoft Mail for Windows,
	group names are expanded on the recipient line, revealing all the members of the
	group.
	
	Situations When Group Names Are NOT Expanded
	--------------------------------------------
	
	With versions 3.0, 3.0b, and 3.2 of Microsoft Mail for Windows, when a message is
	sent to a group that is present in the Postoffice List, the Global Address List
	(GAL), or the Network List, the group names are not expanded. This includes
	groups containing local postoffice users, external postoffice users, and both
	local and external users.
	
	With version 2.1d of Microsoft Mail for Windows, when a message is sent to a
	group that is present in the Postoffice List, the Personal Address List, or the
	Network List, the group names are not expanded. This includes groups containing
	local users, external users, and both local and external users.
	
	Situations When Group Names ARE Expanded
	----------------------------------------
	
	With versions 3.0, 3.0b, and 3.2 of Microsoft Mail for Windows, when a message is
	sent to a group created in the Personal Address Book (PAB), the group name is
	expanded to reveal the friendly names of all the members of the group. This
	occurs only when the group is created in the Personal Address Book and does not
	contain any other groups defined in the Postoffice Address List (PAL), the
	Global Address List, or the Network List. If the group created in the Personal
	Address Book contains other groups that are defined in the Postoffice Address
	List, the Global Address List, or the Network List, the group name is expanded
	to reveal the members of that group, which are other groups; however, these
	member groups are not expanded.
	
	With version 2.1d of Microsoft Mail for Windows, when a message is sent to a
	group of people using version 2.1d or later of Mail for Windows, the version
	2.1d users receive the message with the group name NOT expanded. MS-DOS client
	users with version 3.0 or later also receive the message with the group name NOT
	expanded. Windows client users with version 3.0 or later receive the message
	with the group name expanded. The group name is expanded to reveal the mailbox
	names and not the friendly names of the members of the group.
	
	Additional query words: 2.10d 3.00 3.00b 3.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMail300 kbMail320 kbMail300b
	Version           : WINDOWS:2.1d,3.0,3.0b,3.2
	
	=============================================================================
	

{% endraw %}
