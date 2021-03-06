---
layout: page
title: "Q168801: How to Enable Cluster Logging in Microsoft Cluster Server"
permalink: /kb/168/Q168801/
---

## Q168801: How to Enable Cluster Logging in Microsoft Cluster Server

{% raw %}

	Article: Q168801
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Cluster Server 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Microsoft Cluster Server, you can turn Cluster Logging on as a way of
	troubleshooting problems with the clustering software.
	
	MORE INFORMATION
	================
	
	To enable Cluster Logging, there are two variables you need to place in the
	Windows NT environment variable list. These variables are ClusterLog and
	ClusterLogLevel.
	
	To enter System environment variables, perform these steps:
	
	1. In the System tool in Control Panel, click the Environment tab.
	
	2. Click an entry in the System Environment Variable window.
	
	3. Click the Variable and Value text boxes to clear them.
	
	4. Type "ClusterLog" (without the quotation marks) in the Variable box, type
	  <path>\cluster.log in the Value box, and then click Set, where
	  <path> is the drive and folder to store the Cluster Server log file.
	
	  NOTE: The recommended path is %SystemRoot%\Cluster. For example,
	  C:\WinNT\Cluster\Cluster.log. Cluster logging is enabled by default in
	  Windows 2000, and this is the default path.
	
	5. Type "ClusterLogLevel" (without the quotation marks) in the Variable box,
	  type "0, 1, 2, or 3" (without the quotation marks) in the Value box, and then
	  click Set.
	
	  0=no logging, 1=Errors only, 2=Errors and Warnings, and 3=Everything that
	  happens.
	
	  NOTE: The ClusterLogLevel variable is only used to define the output to the
	  screen when starting the Cluster Service with the /Debug switch. It has no
	  effect on the contents of the Cluster.log.
	
	6. Click OK.
	
	7. Restart your computer for Cluster Server to read the variables correctly.
	
	You can type "SET" (without the quotation marks) at the command prompt to verify
	that you entered the variables correctly after you have restarted the computer.
	
	NOTE: You also have the ability to enter User Variables in the Environment dialog
	box.
	
	The cluster log is set by default to have a maximum size of 8 megabytes (MB).
	When the cluster log reaches its maximum size, it will be truncated by deleting
	the first half of the log file and moving the data in last half of the log file
	to the beginning of the log file. It then continues to fill the log file until
	the maximum size is reached again and then performs the same delete and move
	truncation.
	
	NOTE: Cluster log data is moved in 64KB chunks, therefore the process to truncate
	the log file works as follows:
	
	The first 64KB chunk from the log file is deleted and then the first 64KB chunk
	found after the half way point in the log file is moved to the beginning of the
	log. Then the second 64 KB chunk from the log file will be deleted and the
	second 64KB chunk found after the half way point in the log file will be moved
	to the second 64KB at the beginning of the log. This process will continue until
	the log is only half the maximum size.
	
	NOTE: During this process additional log entries will be buffered and then
	entered when the truncation procedure has completed.
	
	You can increase the maximum log size from the default of 8 MB by adding another
	system environment variable, CLUSTERLOGSIZE, where its value is designated in
	MB. If you set the value of CLUSTERLOGSIZE to 10, the maximum size of the
	cluster log is 10 MB. After you modify the maximum log size, you only have to
	restart the cluster service for the changes to take effect.
	
	Additional query words: cluster group resource mscs
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbAudDeveloper kbClustServSearch
	Version           : :4.0
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
