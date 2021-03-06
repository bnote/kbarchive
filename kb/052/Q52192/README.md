---
layout: page
title: "Q52192: COPY Merges Files If Copied to Nonexistent Directory"
permalink: /kb/052/Q52192/
---

## Q52192: COPY Merges Files If Copied to Nonexistent Directory

{% raw %}

	Article: Q52192
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.x,4.x,5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You use the asterisk (*) wildcard to copy multiple files into a new directory,
	and you receive the following message:
	
	  1 File(s) copied
	
	When you check the new file, it appears that all of your original files have been
	merged into it.
	
	CAUSE
	=====
	
	This behavior is by design. The COPY command does not detect that multiple files
	are being copied to a nonexistent directory.
	
	WORKAROUND
	==========
	
	To avoid this problem, use the XCOPY command when copying multiple files to a
	different directory. If XCOPY detects that multiple files are being copied to a
	nonexistent directory, XCOPY prompts you to create the directory.
	
	MORE INFORMATION
	================
	
	If you use a command similar to
	
	  COPY *.* \MYDIR
	
	when the subdirectory C:\MYDIR does not exist, COPY merges all the files involved
	in the COPY command into one large file. No error message is displayed
	indicating that this has happened. The only immediate sign that the files were
	merged, rather than copied, is that COPY reports the following message, rather
	than indicating the total number of files copied.
	
	  1 File(s) copied
	
	NOTE: If you do not notice that the files have been merged, or if you do not
	check the destination directory for the results of the copy, and you then delete
	the original set of files, only the merged file remains. At this point, it may
	not be possible to separate the merged file into its original component files.
	
	Additional query words: 6.22 3.20 3.21 3.30 3.30a 4.00 4.01 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a
	Version           : MS-DOS:3.x,4.x,5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
