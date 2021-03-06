---
layout: page
title: "Q152225: .Gid File Location Determined by .Cnt File Location in Help"
permalink: /kb/152/Q152225/
---

## Q152225: .Gid File Location Determined by .Cnt File Location in Help

{% raw %}

	Article: Q152225
	Product(s): Microsoft Windows NT
	Version(s): 3.51
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.51 
	- Microsoft Windows NT Server version 3.51 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In some instances, it may be desirable or necessary to have all Help files
	together in a common directory rather than in individual default storage
	locations (such as the system root directory for the Help files shipped with
	Windows NT or the application root directory for the Help files shipped with
	various Windows applications).
	
	If you move only the .hlp files to the new common directory, their associated
	.gid files are created and/or updated in the original directory and not in the
	new common directory, because Windows NT Help creates and/or updates the .gid
	files based on the location of their associated .cnt files.
	
	To ensure that the .gid files are updated in the new common directory, move the
	related .cnt files to the new common directory and either move the current .gid
	files to the new common directory (in which case they are updated in the common
	directory) or delete them from the original directory (in which case they will
	be re-created in the new common directory).
	
	MORE INFORMATION
	================
	
	Windows NT 3.51 uses a Help engine based on the Windows 95 Help engine. With
	this Help engine comes the implementation of several new support files (listed
	below) in addition to the standard Help files (.hlp).
	
	FTS
	---
	
	Files of this type contain key words and/or phrases for full-text search queries.
	If such a file does not exist for the base Help file being opened by Help, you
	are prompted to create one by the Find Setup Wizard.
	
	CNT
	---
	
	Files of this type enable the use of multiple help file grouping for the Help
	Topics dialog box by providing the indexes to the relevant Help files.
	
	FTG
	---
	
	Files of this type are generated by the Help engine when a Help file is opened
	for which a .cnt file exists. They contain the data necessary for cross-file,
	full-text Help file searches.
	
	GID
	---
	
	Files of this type are hidden files generated by the Help engine when a search is
	performed in a Help file. These .gid files contain the indexes displayed on the
	Index tab of the Help Topics dialog box.
	
	NOTE: Files of the type .ind (full text search index), used by earlier versions
	of Windows NT Help, are no longer used or supported by the new Help engine.
	
	
	To ensure that all Help-related files are in a common directory, move all of the
	above defined files, along with the .hlp files, to the new location (with the
	possible exception of the .gid files, which can be deleted, as noted in the
	Summary section above).
	
	NOTE: To ensure that Windows NT Help can locate these files in their new
	location, update the path environment variable to include the new common
	directory, by using the System Control Panel.
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS351search
	Version           : 3.51
	
	=============================================================================
	

{% endraw %}
