---
layout: page
title: "Q87176: Associating .EXE, .COM, or .BAT Files with MS-DOS Shell"
permalink: /kb/087/Q87176/
---

## Q87176: Associating .EXE, .COM, or .BAT Files with MS-DOS Shell

{% raw %}

	Article: Q87176
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:4.x,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 4.0, 4.01, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you are creating batch programs, you might find it useful to associate the
	.BAT extension with a text editor (for example, MS-DOS Editor). So when you
	double-click on a .BAT file in an MS-DOS Shell file list, Editor will run and
	load that batch file.
	
	However, if you associate a program with an .EXE, .COM, or .BAT extension, you
	will be unable to run program files that have the associated extension by
	double-clicking on the file in Shell's file list or by selecting the file and
	choosing Open from the File menu.
	
	To run a program file that has an associated extension, create a program item to
	start the program file. If you are using MS-DOS version 5.0 or 6.0, you can also
	use the Run command from the File menu.
	
	MORE INFORMATION
	================
	
	MS-DOS 4.x
	----------
	
	MS-DOS 4.x Shell allows you to associate the .BAT extension with a program. You
	cannot associate .COM or .EXE extensions.
	
	If you associate a program with a .BAT extension, you will be unable to run a
	batch file by double-clicking on it in the file list or by selecting the file
	and choosing Open from the File menu. To run a program file with a .BAT
	extension, create a program item for the program.
	
	MS-DOS 5.0, 5.0a, and 6.0
	-------------------------
	
	MS-DOS 5.0 or 6.0 Shell allows you to associate a .EXE, .COM, or .BAT extension
	with a program.
	
	If you associate a program with an .EXE, .COM, or .BAT extension, you will be
	unable to run program files that have the associated extension by
	double-clicking on the file in the file list or by selecting the file and
	choosing Open from the File menu. To run a program file that has an associated
	extension, use the Run option from the File menu or create a program item for
	the program.
	
	REFERENCES
	==========
	
	"Microsoft MS-DOS User's Guide and Reference," versions 5.0 and 5.0a, pages
	58-60
	
	For more information on the Associate command in MS-DOS 4.0, 4.01, and 4.01a,
	see:
	
	"Microsoft MS-DOS Shell User's Guide," versions 1, page 77-79
	
	Additional query words: 4.00 4.00a 4.01 4.01a 5.00 5.00a 6.00 dosshell
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS400 kbMSDOS600 kbMSDOS500 kbMSDOS401 kbMSDOS500a
	Version           : MS-DOS:4.x,5.0,5.0a,6.0
	
	=============================================================================
	

{% endraw %}
