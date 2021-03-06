---
layout: page
title: "Q305007: XCON: You Cannot Send SMTP Mail Through a Firewall"
permalink: /kb/305/Q305007/
---

## Q305007: XCON: You Cannot Send SMTP Mail Through a Firewall

{% raw %}

	Article: Q305007
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 27-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you send a message to a Simple Mail Transfer Protocol (SMTP) recipient over
	the Internet Mail Service by using Microsoft Outlook Express or any other Post
	Office Protocol version 3 (POP3) or Internet Message Access Protocol Version
	4rev1 (IMAP4) client, you may receive a non-delivery report (NDR) that is
	similar to:
	
	  The message could not be sent because one of the recipients was rejected by
	  the server. The rejected e-mail address was 'XXX@XXX.XXX'. Subject 'XXXX',
	  Account: 'XXX', Server: 'XXX.XXX.XXX.XXX', Protocol: SMTP, Server Response:
	  '550 Requested action not taken: mailbox unavailable', Port: 25, Secure(SSL):
	  No, Server Error: 550, Error Number: 0x800CCC79
	
	CAUSE
	=====
	
	This issue may occur if:
	
	- Rerouting is selected on the Routing tab of the Internet Mail Service.
	
	-and-
	
	- The "Hosts and clients that successfully authenticate" routing restriction is
	  selected.
	
	-and-
	
	- A Watchguard Firebox firewall is being used.
	
	The Watchguard Firebox firewall can be configured to strip SMTP commands. To use
	authentication, the following command verbs must be turned on:
	
	- Auth
	
	- Auth-logon
	
	If the authentication headers are denied on the firewall, the mail flow is
	stopped externally.
	
	RESOLUTION
	==========
	
	To resolve this issue, configure the firewall to allow all of the Exchange
	Server SMTP command verbs to pass through. If you have to, turn off the headers
	that are being stripped one by one.
	
	MORE INFORMATION
	================
	
	Determine whether or not you can successfully send mail from a POP3 or IMAP4
	client if you connect directly to the Exchange Server computer, instead of
	connecting through the firewall.
	
	Additional query words: IMS
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
