---
layout: page
title: "Q80301: How to Change the MS-DOS Cursor"
permalink: /kb/080/Q80301/
---

## Q80301: How to Change the MS-DOS Cursor

{% raw %}

	Article: Q80301
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:2.x,3.x,4.x,5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 2.11, 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	There is no way to change the appearance of the command line cursor in MS-DOS
	with any MS-DOS command. The cursor is a function of the BIOS and can only be
	modified through a ROM BIOS call. There are third party applications that
	facilitate this, such as Norton Utilities and PC Tools. You can also access the
	BIOS and modify the cursor by using the MS-DOS Debug utility.
	
	MORE INFORMATION
	================
	
	You can write a short program to modify the MS-DOS cursor. One way to do this is
	by creating and executing a short Debug script. The changes made are temporary
	in memory. Therefore, if the goal is to have the cursor altered at all times, it
	will be necessary to insert a line in the AUTOEXEC.BAT file to call the cursor
	program on boot.
	
	To change the appearance of the MS-DOS cursor, enter the following at the command
	prompt:
	
	Command Prompt          Enter This
	--------------          ----------
	
	C:\>                    debug <press ENTER>
	-                       a100 <press ENTER>
	287E:0100               mov ah,01 <press ENTER>
	287E:0102               mov cx,010n <press ENTER>  (n range=1-4)
	287E:0105               int 10 <press ENTER>
	287E:0107               int 20 <press ENTER>
	287E:0109               <press ENTER>
	-                       n C:\cursor.com <press ENTER>
	-                       rcx <press ENTER>
	CX 0000
	:                       9 <press ENTER>
	-                       w <press ENTER>
	Writing 00009 bytes
	-                       q <press ENTER>
	
	C:\>
	
	Changing the value of n (1-4) will result in different appearances for the
	cursor, where n=4 is a large cursor.
	
	Insert the following line in the AUTOEXEC.BAT file to have the cursor loaded upon
	booting the machine:
	
	  c:\cursor.com
	
	Note: This procedure relies on standard IBM ROM BIOS services and therefore
	cannot be guaranteed to work on all systems. This information is only provided
	as a possible solution.
	
	The products included here are manufactured by vendors independent of Microsoft;
	we make no warranty, implied or otherwise, regarding these products' performance
	or reliability
	
	Reference(s):
	
	"The NEW Peter Norton Programmer's Guide to the IBM PC & PS/2," Microsoft
	Press, 1988
	
	
	Additional query words: 3.3 3.3a 3.30 3.30a 4.0 4.0a 4.00 4.00a 4.01 4.01a 5.00 noupd
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS211
	Version           : MS-DOS:2.x,3.x,4.x,5.0
	
	=============================================================================
	

{% endraw %}
