---
layout: page
title: "Q173573: WinNT 4.0 Post SP3 Hotfix Can Cause Stop 0x1E in Win32k.sys"
permalink: /kb/173/Q173573/
---

## Q173573: WinNT 4.0 Post SP3 Hotfix Can Cause Stop 0x1E in Win32k.sys

{% raw %}

	Article: Q173573
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you install Double Click or Java Post Service Pack 3 (SP3) hotfixes, the
	system blue screens with a stop error message in Win32k.sys:
	
	  STOP: 0x0000001e (0xc000001d, 0x00000023, 0x00000000, 0x00000000)
	
	The first parameter is consistently 0xc000001d, the remaining parameters have
	varied.
	
	The STOP screen occurs before you can attempt to uninstall the hotfix.
	
	CAUSE
	=====
	
	Installing the Post SP3 hotfix Double Click or Java after the GetAdmin hotfix
	causes the Win32k.sys file to be incompatible with the kernel.
	
	The Win32k.sys file furnished with the Double Click hotfix and the Java hotfix is
	not compatible with the kernel furnished with the GetAdmin hotfix. The
	Win32k.sys file furnished with the GetAdmin hotfix is dated 7/12/97. The
	versions of Win32k.sys supplied with the other hotfixes have earlier dates.
	
	RESOLUTION
	==========
	
	Replace the Win32k.sys file with the version from the GetAdmin hotfix, dated
	7/12/97.
	
	If the operating system is installed on a FAT partition, this can be accomplished
	by starting the system with a DOS boot floppy disk and copying the correct
	Win32k.sys from the most recently installed hotfix uninstall directory to the
	System32 directory.
	
	The Double Click hotfix uninstall directory is $NTUninstallQ170510$. The Java
	hotfix uninstall directory is $NTUninstallQ168748$. Both reside under the system
	root directory, usually called \Winnt.
	
	If the operating system is installed on an NTFS partition, a parallel
	installation of the operating system can be done and the file can be replaced in
	the manner described above while you are booted to the parallel installation.
	
	If a parallel installation is not possible (for example, there is insufficient
	disk space), perform the following steps:
	
	1. Make a copy of the current Emergency Repair Disk (ERD).
	
	2. Delete the registry hives from the ERD you just copied (this is required in
	  order to make sufficient space for the Win32k.sys file on the disk).
	
	3. Copy the correct version of the Win32k.sys file to the root of the ERD (the
	  file can be obtained by running the hotfix with the /x option on a system
	  running Windows NT 4.0. This extracts the files without installing the fix).
	
	4. Change the attributes of the Setup.log file on the ERD (use the attrib - s -h
	  -r Setup.log command).
	
	5. Add the following information to the BEGINNING of the section:
	
	     [Files.WinNt]:
	
	        \Winnt\System32\Win32k.sys = "win32k.sys","12d370","\","nt40 repair
	        disk","win32k.sys"
	
	6. Run the Emergency Repair Procedure, verifying system files only.
	
	7. When prompted, replace the Win32k.sys file.
	
	8. After replacing the Win32k.sys file, exit setup. This leaves the other files
	  intact.
	
	9. Restart the system.
	
	For more information on replacing system files using a modified Emergency Repair
	Disk see the following Microsoft Knowledge Base article:
	
	ARTICLE-ID: Q164471
	TITLE : Replacing System Files Using a Modified Emergency Repair Disk
	
	Additional query words: 0X1E
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
