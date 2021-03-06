---
layout: page
title: "Q171049: XADM: Error Msg. Trying to Modify E-mail Address in Admin"
permalink: /kb/171/Q171049/
---

## Q171049: XADM: Error Msg. Trying to Modify E-mail Address in Admin

{% raw %}

	Article: Q171049
	Product(s): Microsoft Exchange
	Version(s): 5.00
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 25-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to modify the E-mail address of a mailbox in the Administrator
	program, you may get a pop-up dialog box with the following error message:
	
	  System attendant is not responding. Please check if System attendant is
	  running.
	  The system attendant service may be paused, or the version is not fitting
	  the version of exchange admin program.
	
	When you try to access the property pages of the Internet Mail Service, you may
	get one of the following error messages:
	
	- 
	
	  Extension SMTP could not be loaded. The MSExchangeSA service is not
	  available. MS Exchange Admin ID No C1031668
	
	- 
	
	  Extension SMTP could not be loaded. An error occurred, file replication
	  extension.dll file with the incorrect version number.
	
	You also may find one or both of the following error messages in the event
	viewer:
	
	   Error 1702 Error just occurred while writing delivery log information 
	    to the MSExchangeSA.
	
	   Internal MTA error occurred. Please contact MS Product Support
	    Service. Unable to write the Message Tracking log.
	   [BASE XFER-N 22 88](16)
	
	When you check Control Panel\Services, the system attendant (SA) is shown as
	still running. If you stop the Exchange Administrator program and check the
	system attendant service again, you discover that the SA service has stopped. If
	you try to start the system attendant, it starts fine.
	
	CAUSE
	=====
	
	This problem usually happens after you apply Service Pack 1 to Exchange Server
	5.0. The application of the service pack may have failed or was interrupted.
	While this problem exists, other functions of Exchange Server seem to be
	working.
	
	WORKAROUND
	==========
	
	Perform the following steps to fix this problem:
	
	1. Disable or remove any third-party applications such as Norton PC Anywhere32
	  or Netscape Communicator.
	
	2. Confirm that the Exchange Server computer has enough free disk space, and
	  there are no interrupt request (IRQ) conflicts.
	
	3. In Control Panel \ Services, select the system attendant service and click
	  the Startup button. Verify the correct Startup service account, delete and
	  re-type the password, and confirm the password.
	
	4. Increase the diagnostic logging on the directory, the information store, and
	  the MTA Exchange services.
	
	5. Confirm that there is no corruption in the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeSA
	
	  You confirm this by comparing the Exchange Server computer that is having the
	  problem with the registry of another Exchange Server 5.0 computer that is
	  working properly.
	
	6. Stop all the Exchange services and the Exchange Administrator program.
	
	7. Reapply Exchange Server 5.0 Service Pack 1. If the Service Pack fails again,
	  perform step 8; otherwise go to step 9.
	
	8. Expand the SP1 files on another computer, and then copy them over the
	  existing files in the c:\exchsrvr\bin and c:\exchsrvr\addins directories of
	  the Exchange Server computer that is having the problem.
	
	9. If you get sharing violations, confirm that the c:\exchsrvr is shared and the
	  group Everyone has full control. Stop sharing the root folders of drive C:\
	  and drive D:\, and then click the Apply button. Share these two folders
	  again, and click Apply again. For some reason, and in at least one case, this
	  stopping and restarting of the sharing seems to avoid this sharing violation
	  error message.
	
	10. Run the SP1 update again, and then confirm that the registry key mentioned
	  above was updated successfully.
	
	11. Change the Startup of all the Exchange services to automatic and restart the
	  Exchange Server computer.
	
	12. Verify that the problem is fixed by starting the Exchange Administrator
	  program and confirming that you can modify the E-mail address of one mailbox
	  successfully.
	
	MORE INFORMATION
	================
	
	Step number 9 above might fail with a different error message. The following
	error message may be received:
	
	  There was an internal error and one of the windows you have been
	  using have been closed. CsetupWebCon.ins file could not be found
	  at or near line 19. Reboot your exchange server.
	
	If you receive this error message, ignore it and continue the workaround steps as
	mentioned above.
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : 5.00
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
