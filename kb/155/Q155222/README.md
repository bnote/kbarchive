---
layout: page
title: "Q155222: How to Determine the ARC Path"
permalink: /kb/155/Q155222/
---

## Q155222: How to Determine the ARC Path

{% raw %}

	Article: Q155222
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you troubleshoot some issues where a Windows NT boot disk is needed, you
	may need the ARC path for the Boot.ini file. However, it may not be obvious, or
	the machine administrator may not remember the partition or root directory the
	operating system was installed in. This information can be recovered from the
	Emergency Repair Disk.
	
	MORE INFORMATION
	================
	
	The Setup.log file is located on the Emergency Repair Disk. It has the system,
	hidden, and read-only attributes. If this file is opened in a text editor, the
	first few lines will provide information about how to build the ARC path to the
	operating system. The following is an excerpt from a typical Setup.log file.
	
	  [Paths]
	  TargetDirectory = "\WINNT"
	  TargetDevice = "\Device\Harddisk0\partition2"
	  SystemPartitionDirectory = "\"
	  SystemPartition = "\Device\Harddisk0\partition1"
	
	A typical ARC path might be:
	
	  multi(0)disk(0)rdisk(0)partition(2)\WINNT="My Server 4.0"
	
	The rdisk parameter is defined as Harddisk<X> on the TargetDevice line,
	where <X> is a variable that represents the drive ordinal. Note that the
	rdisk parameter is not used when SCSI replaces multi in the ARC path.
	
	The partition parameter is defined as partition<X> on the TargetDevice
	line, where <X> is a variable that represents the partition ordinal. Note
	also that SystemPartition refers to the partition where NTLDR is stored. Use
	TargetDevice for the partition ordinal value.
	
	The TargetDirectory line defines the system root directory, which is the part of
	the ARC path immediately following the partition number.
	
	For more information, please see the following articles in the Microsoft
	Knowledge Base:
	
	ARTICLE-ID: Q119467
	TITLE : Creating a Boot Disk for an NTFS or FAT Partition
	
	ARTICLE-ID: Q102873
	TITLE : Boot.ini and ARC Path Naming Conventions and Usage
	
	ARTICLE-ID: Q130921
	TITLE : Creating an FT Boot Disk With SCSI() and Multi() Identifiers
	
	ARTICLE-ID: Q139333
	TITLE : Creating Alternate Boot Selections on AXP Machines
	
	Additional query words: RISC prodnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
