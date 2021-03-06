---
layout: page
title: "Q178844: XADM: How to Generate Reports on Mailbox Resources"
permalink: /kb/178/Q178844/
---

## Q178844: XADM: How to Generate Reports on Mailbox Resources

{% raw %}

	Article: Q178844
	Product(s): Microsoft Exchange
	Version(s): 4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 18-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Exchange Administrator program, version 5.5, can export mailbox or
	public folder resource reports to a .CSV file. The version 5.5 Administrator
	program has this capability even when run against Exchange 4.0 or 5.0 Servers.
	
	Mailbox and public folder resource usage, including total number of messages and
	message size per mailbox or folder, are displayed in the Administrator program
	at:
	
	  Configuration, Servers, <Servername>, Private Information Store,
	  Mailbox Resources
	
	and
	
	  Configuration, Servers, <Servername>, Public Information Store, Public
	  Folder Resources
	
	Prior to version 5.5, Exchange Server relied on Crystal Reports to provide such
	reporting. This article explains both how to use either Crystal Reports or the
	version 5.5 Exchange Administrator program to generate resource reports.
	
	MORE INFORMATION
	================
	
	To generate a report in Exchange Server 5.5 through the Administrator program,
	do the following:
	
	NOTE: If you start Exchange Server in Raw mode, these steps do not work.
	
	1. In the Administrator program, go to Servers, Servername, and open the Mailbox
	  Resources window for the server.
	
	2. Highlight an entry on the right side of the screen.
	
	3. Select "Save Window Contents" from the File menu. After this information is
	  saved to a file, that file can be manipulated with a database or spreadsheet
	  program to generate custom reports.
	
	Crystal Reports must be installed from the Microsoft BackOffice 97 Resource Kit.
	It is located in the Exchange\winnt\I386\Admin\Crystal directory. To install it,
	double-click on the CRWINTEL installation icon.
	
	To generate a report on the mailbox resources in use by a particular server from
	Crystal Reports, do the following:
	
	1. Run CRW32 from the directory where you installed the application.
	
	2. Select File/New/Standard Expert from the menu bar.
	
	3. Click Exchange Data at the Step 1 prompt "Choose data to report on."
	
	4. The Log On Server box will appear. Select Mailbox Admin and click OK.
	
	5. The Logon to Exchange Servers box will appear. Click Select Servers, and
	  select the server to be reported on.
	
	6. Click Select Profiles, and select a profile to be used. This profile must
	  have the permissions to access this information.
	
	7. Click Done.
	
	8. In the Choose SQL Table window, the Mailbox Admin Table should be
	  highlighted. Click Add.
	
	9. Click Done.
	
	10. Click Next.
	
	11. From Property Fields, double-click Mailbox and Total Message Size (Byte).
	
	12. Click Next.
	
	13. In Report Fields:, the Admin Table: Mailbox should be selected. Click Add.
	
	14. Click Next three more times. On the Style tab, enter the Title of the
	  report.
	
	15. Click Preview Report.
	
	16. Select File/Print Preview from the menu. The following message will be
	  displayed:
	
	  This program is a limited version of Crystal Reports. To generate
	  reports on multiple servers, please contact Crystal Reports for the
	  latest "Full" version and instructions on how to generate the
	  reports.
	
	Additional query words: export public folder message size limits
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : :4.0,5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
