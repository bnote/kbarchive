---
layout: page
title: "Q101791: Musical Instruments: Manual Installation Instructions"
permalink: /kb/101/Q101791/
---

## Q101791: Musical Instruments: Manual Installation Instructions

{% raw %}

	Article: Q101791
	Product(s): Microsoft Home Multimedia Titles
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Musical Instruments for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides instructions to manually install Microsoft Musical
	Instruments version 1.0.
	
	MORE INFORMATION
	================
	
	These instructions assume:
	
	- Your hard disk is drive C
	
	- Your destination folder is C:\Msinstr
	
	- Your Windows folder is C:\Windows
	
	- Your CD-ROM drive is drive D
	
	If your hard disk drive, destination folder, Windows folder, or CD-ROM drive
	letters are different, replace the drive letters and folder names throughout
	this article with the drive letters and folder names on your computer.
	
	NOTE: The following instructions discuss copying, editing, and modifying folders
	and files. For more information about accomplishing these tasks in Windows, see
	your Windows printed documentation or online Help.
	
	1. Create a folder named Msinstr on the hard drive (C:\Msinstr).
	
	  For example, type the following at the MS-DOS command prompt and press ENTER
	  at the end of the line:
	
	  "md c:\msinstr" (without the quotation marks)
	
	2. Copy all files in the D:\Bin folder to the C:\Msinstr folder. The files are:
	
	  - Mi.hlp
	  - Msinstr.exe
	  - Msinstr.the
	
	  For example, type the following at the MS-DOS command prompt and press ENTER:
	
	  "copy d:\bin\*.* c:\msinstr" (without the quotation marks)
	
	  NOTE: On later versions (9/93) of Musical Instruments, the Bin folder has been
	  replaced with the Xfiles folder. If your CD-ROM has a Xfiles folder,
	  substitue Xfiles for Bin in this step.
	
	3. Copy Readme.txt from the D:\ folder to C:\Msinstr.
	
	4. If you are using Windows 3.1x, copy the following files from D:\Drivers to
	  C:\Windows\System:
	
	  - Msacm.drv
	  - Msadpcm.acm
	
	  NOTE: Do not perform this step if you are using Windows 95 or Windows NT.
	  Allowing system files to be overwritten in Windows 95 or Windows NT may cause
	  improper system performance.
	
	5. Use a text editor, such as Microsoft Notepad, to make the following changes
	  to the Msinstr.ini file, which is located in the Windows folder. If the
	  Msinstr.ini file does not already exist, create one in the Windows folder
	  with these entries:
	
	        [Music]
	        CD=D:
	        Command=C:\msinstr\msinstr.the
	        Window=62,24
	
	6. Use a text editor to make the following changes to this Windows
	  initialization file, which is located in the Windows folder:
	
	  Changes to the System.ini File
	  ------------------------------
	
	        [Drivers]
	        wavemapper=msacm.drv
	
	        [MSACM]
	        install=msadpcm.acm
	
	7. Add the Musical Instruments icons or shortcuts by following the appropriate
	  instructions at the end of this article.
	
	8. Exit Windows and restart the computer. The installation is now complete.
	
	Creating the Start Menu Shortcuts
	---------------------------------
	
	If you are using Windows 95, add Musical Instruments to the Start Menu by
	following these instructions:
	
	1. Click the Start button, point to Settings, and then click the Taskbar.
	
	2. Click the Start Menu Programs tab.
	
	3. Click Add.
	
	4. Type the following in the Command Line box, and then click Next:
	
	  "c:\msinstr\msinstr.exe" (without the quotation marks)
	
	5. In the Select Program Folder dialog box, click the Microsoft Multimedia
	  folder to select it, and then click Next.
	
	  NOTE: If the Microsoft Multimedia folder, create it using the following
	  steps:
	  a. Click New Folder
	
	  b. Type the following, and then click Next:
	
	  "Microsoft Multimedia" (without the quotation marks)
	
	6. In the Select A Title For The Program dialog box, type the following, and
	  then click Finish:
	
	  "Musical Instruments" (without the quotation marks)
	
	Creating Program Manager Icons
	------------------------------
	
	If you use the Windows Program Manager, create the Musical Instruments icons
	using the following instructions:
	
	1. Open the Microsoft Multimedia group. If this group does not already exist,
	  create it as follows:
	  a. On the File menu, click New.
	
	  b. Click Program Group, and then click OK.
	
	  c. In the Description box, type the following, and then click OK:
	
	  "Microsoft Multimedia" (without the quotation marks)
	
	2. Create the following two items in the Microsoft Multimedia group. To create
	  an item, choose New from the Program Manager File menu, then select Program
	  Item and choose OK. Enter the following information into the fields of the
	  Program Item Properties dialog box, then choose OK:
	
	  Item 1:
	  Description:     Musical Instruments
	  Command Line:    C:\MSINSTR\MSINSTR.EXE
	
	  Item 2:
	  Description:     Musical Instruments-Read Me
	  Command Line:    notepad.exe c:\msinstr\readme.txt
	
	Additional query words: 1.00 multi media multimedia multi-media manual install set up setup installation installing Crun set-up setting-up configure installer installations
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeProdSearch _IKkbbogus kbZNotKeyword kbMusicalInst
	Version           : WINDOWS:1.0
	
	=============================================================================
	

{% endraw %}
