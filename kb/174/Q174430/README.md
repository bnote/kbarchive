---
layout: page
title: "Q174430: Kids Plus!: Play It and Talk It Missing Required .DLLs"
permalink: /kb/174/Q174430/
---

## Q174430: Kids Plus!: Play It and Talk It Missing Required .DLLs

{% raw %}

	Article: Q174430
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): kbenv kbimu kbSysSettings
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Plus! for Kids, version 1.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, you should first make a backup copy of the
	registry files (System.dat and User.dat). Both are hidden files located
	in the Windows folder.
	
	SYMPTOMS
	========
	
	After installing Plus! For Kids you are unable to run Play It! or Talk It!
	because the programs are unable to find required .dll files.
	
	CAUSE
	=====
	
	This occurs if the path to the files in the Windows registry is incorrect.
	
	The following files are associated with this problem:
	
	  Mediagal.dll - (Paint It!/Picture Picker)
	  Mmmidi16.dll - (Play It!)
	  Mmmidi32.dll - (Play It!)
	  Mnmidi32.dll - (Play It!)
	  Tibase32.dll - (Talk It!)
	  Tieng32.dll - (Talk It!)
	  Tispan32.dll - (Talk It!)
	
	RESOLUTION
	==========
	
	Use Method 1 below to resolve the problem. If Method 1 does not resolve the
	problem, use Method 2.
	
	Method 1
	--------
	
	Copy all seven of the files listed above from the Plus! For Kids compact disc to
	the Windows\System folder on your hard disk. If the program does not run after
	you have copied the files, try Method 2.
	
	
	For more information about how to copy files in Windows, please refer to your
	printed Windows documentation or online Help.
	
	Method 2
	--------
	
	If the program still does not run you will need to edit the Windows registry to
	remove the incorrect entries and resolve the problem.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editorcan be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it. If
	you are running Windows NT, you should also update your Emergency Repair Disk
	(ERD).
	
	To resolve this issue, delete the (Default) and Path Key registry entries
	contained in the following registry keys:
	
	     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
	     \App Paths\PaintIt!.EXE
	
	     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
	     \App Paths\PictPick.EXE
	
	     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
	     \App Paths\PlayIt!.EXE
	
	     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
	     \App Paths\TalkIt!.EXE
	
	When you start each of these programs, the program looks in the Windows\System
	folder to start the program and adds the missing entries to the registry.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Plus! For Kids version
	1.0.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbimu kbSysSettings 
	Technology        : _IKkbbogus kbGamesSearch kbPlusKids kbPlusSearch
	Version           : WINDOWS:1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
