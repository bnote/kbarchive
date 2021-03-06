---
layout: page
title: "Q184693: DNS/DHCP/WINS Release Notes for Windows NT 4.0 SP4 Update"
permalink: /kb/184/Q184693/
---

## Q184693: DNS/DHCP/WINS Release Notes for Windows NT 4.0 SP4 Update

{% raw %}

	Article: Q184693
	Product(s): Microsoft Windows NT
	Version(s): 4.0 SP4
	Operating System(s): 
	Keyword(s): kbFEA kbWinNT400sp4fea
	Last Modified: 23-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 SP4 
	- Microsoft Windows NT Server version 4.0 SP4 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 SP4 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SUMMARY
	=======
	
	Domain Name System (DNS)
	------------------------
	
	This service pack update release includes several fixes to correct known Domain
	Name System (DNS) problems reported for Microsoft Domain Name System (DNS)
	Server and DNS Manager.
	
	These fixes address specific problems fully described in the following articles
	in the Microsoft Knowledge Base:
	
	  
	
	
	  Article-ID: Q129047
	  Title : Synchronizing DNS Information in Registry with Boot Files
	
	  Article-ID: Q142047
	  Title : Bad Network Packet May Cause Access Violation (AV) on DNS Server
	
	  Article-ID: Q154984
	  Title : DNS Server May Not Recursively Resolve Some Names
	
	  Article-ID: Q154985
	  Title : DNS Registry Key Not Updated When Changing Zone Type
	
	  Article-ID: Q159310
	  Title : Updated Version of Dns.exe Fixes Several Problems
	
	  Article-ID: Q164300
	  Title : DNS Registry Parameter - AddressAnswerLimit
	
	  Article-ID: Q167629
	  Title : Predictable Query IDs Pose Security Risks for DNS Servers
	
	  Article-ID: Q169461
	  Title : Access Violation in DNS.EXE Caused by Malicious Telnet Attack
	
	  Article-ID: Q170518
	  Title : DNS Admin Fails When Managing Large Number of Zones
	
	  Article-ID: Q173676
	  Title : Client Cannot Resolve MX Record via Microsoft DNS Server
	
	  Article-ID: Q182227
	  Title : DNS Server Does Not Check for Delegations Before Forwarding
	
	  Article-ID: Q182713
	  Title : Multiple Entries in Zone File Cause Memory Leak in Dnsadmin.exe
	
	  Article-ID: Q184881
	  Title : Reverse Lookups with BIND Earlier Than 4.8.3 Fail
	
	  Article-ID: Q185734
	  Title : DNS Server Access Violation in Dns!sendNbstatResponse Routine
	
	  Article-ID: Q185816
	  Title : DNS Server Event Log IDs Incorrect After Applying SP4
	
	  Article-ID: Q186820
	  Title : DNS Server Returns Wrong Response When WINS Lookup Is Enabled
	
	  Article-ID: Q187800
	  Title : NSLOOKUP Fails to Return DomainName Option for DHCP Client
	
	Dynamic Host Configuration Protocol (DHCP)
	------------------------------------------
	
	This service pack update release includes several quality improvement fixes to
	correct known Dynamic Host Configuration Protocol (DHCP) problems reported for
	Microsoft DHCP Server, the DHCP Manager administration tool, and for Microsoft
	DHCP-enabled clients running under earlier released versions of Windows NT 4.0.
	
	These fixes address specific problems fully described in the following articles
	in the Microsoft Knowledge Base:
	
	  Article ID: Q194424
	  Title : DHCP Server May Fail to Record Lease
	
	  Article-ID: Q141496
	  Title : DHCP Client Comment Disappears When Obtaining IP Address
	
	  Article-ID: Q163055
	  Title : DHCP Client May Fail With WinNT 4.0 SP2 Multinetted DHCP Server
	
	  Article-ID: Q167708
	  Title : BOOTP Client Names Disappear in DHCP Manager
	
	  Article-ID: Q173753
	  Title : Duplicate IP Addresses After Upgrading Clients to SP2
	
	  Article-ID: Q175035
	  Title : Diskless Workstations Cannot Find BOOTP Server With DHCP
	
	  Article-ID: Q177357
	  Title : DHCP Client Does Not Immediately Renew Address
	
	  Article-ID: Q182047
	  Title : DHCP Server Performance Degraded By Large Number of Scopes
	
	  Article-ID: Q183875
	  Title : DHCP Server Leases Excluded Addresses if the Scope Is Expanded
	
	
	  Article-ID: Q187802
	  Title : DHCP Assigns "Bad_Address" to "Host Unreachable"
	
	  Article-ID: Q188027
	  Title : Performance, Audit Logging, and Fixes to the DHCP Service
	
	  Article-ID: Q184353
	  Title : DHCP ALT+H Shortcut Key for HELP Is Not Available
	
	  Article-ID: Q189283
	  Title : No More Than About 570 Reservations Visible in a DHCP Scope
	
	  Article-ID: Q193436
	  Title : DHCP Client Shuts Down After Two Declines
	
	  Article-ID: Q190552
	  Title : WinNT 4.0 DHCP Client Modified to meet RFC 2131
	
	  Article-ID: Q184744
	  Title : DHCP Server Leaks Registry Quota on Alpha Version of Windows NT
	
	  Article-ID: Q184344
	  Title : Reconcile on DHCP Scope Does Not Work Correctly for BOOTP Client
	
	  Article-ID: Q169291
	  Title : Using Scopes with Different Subnet Masks in a Superscope
	
	You can obtain the specific article from Microsoft Support Online
	(http://msdn.microsoft.com/support).
	
	Windows Internet Name Service (WINS)
	------------------------------------
	
	Windows NT Server includes the following added features for this service update
	release to Windows Internet Name Service (WINS) and WINS Manager:
	
	- Manual removal of dynamic WINS database records.
	
	- Multi-select operations for WINS database records.
	
	- Burst mode handling for WINS servers.
	
	WINS Manager
	------------
	
	WINS Manager now provides improved database management through support for record
	multi-selection and the ability to remove dynamic-type WINS records from the
	WINS server database.
	
	Manual Removal of Dynamic WINS Database Records:
	
	The ability to manually delete dynamically-registered names mappings from the
	WINS database is now a part of WINS Manager. Because this support was not
	provided in previous versions of WINS Manager, deletion was difficult, requiring
	the advanced use of certain command line tools, such as Winscl.exe, a tool
	provided by the previous Windows NT Server resource kits.
	
	NOTE: Dynamic mappings are added to the WINS database when clients start and
	register their names in WINS before joining the network. Static mappings are
	administratively added to the WINS database by a network administrator and can
	be edited or removed in the same manner.
	
	Deletion is a useful practice for clearing up problems where dynamic WINS records
	are not fully consistent with currently stored mappings that have been
	replicated to other remote WINS servers. In addition, by allowing deletion of
	dynamic WINS mappings, WINS administrators can eliminate the practice of using
	static WINS mappings to correct name resolution problems which can create
	further problems for WINS.
	
	NOTE: The use of static WINS mappings is not recommended for clients that can
	directly perform dynamic registration of their names in WINS. Where static
	mappings are used to resolve connectivity issues and provide domain logon
	support for WINS clients, these mappings can cause additional problems or be
	difficult to fully remove from large WINS installations with multiple points of
	replications.
	
	You can delete records in two ways: simple deletion or tombstoned deletion. With
	simple deletion, the selected WINS records are only removed from the selected
	WINS server that is actively being managed using WINS Manager. With simple
	deletion, records that are deleted are not removed or modified on other WINS
	servers. This method can be useful for making a "quick deletion" of selected
	records on a single WINS server. For this method of deletion to be effective,
	you must make certain that the deleted records do not still appear on other WINS
	servers used in replication.
	
	NOTE: If records are removed from a server using simple deletion but still exist
	in WINS data on other servers, the deleted records may reappear on the server
	where deletion was made when replication next occurs with other WINS servers.
	
	Perform the following steps to use simple or tombstoned deletion:
	
	1. Start WINS Manager.
	
	2. Click Mappings, and then click Show Database.
	
	3. Select the records you want to delete or tombstone.
	
	4. Click Delete Mapping. The Confirm Deletion dialog box appears.
	
	5. For Operation, click Delete to perform simple deletion of the records on the
	  selected WINS server or Tombstone to tombstone the records for eventual
	  deletion of the records on all WINS servers.
	
	6. If a single record is selected, click Yes to delete. If multiple records are
	  selected, click Yes to All to delete all selected records.
	
	How Tombstoning Works
	---------------------
	
	With tombstoning, the "tombstoned" records are marked as extinct on the WINS
	server and immediately removed from active use by the server for WINS name
	resolution. However, these mappings are not immediately deleted from the
	server's database. Instead, the tombstoned records remain present for
	replication purposes so that other WINS servers are notified as well that these
	records are inactive in WINS. After the deleted records are marked as tombstoned
	on all WINS servers where they have been replicated, the records will then be
	removed during subsequent scavenging operations performed on each server.
	
	To use tombstoning effectively, you should only tombstone WINS records on the
	WINS server that is the original owner for the records to be deleted.
	
	IMPORTANT: In most cases, WINS records should be tombstoned at the original
	owning WINS server to prevent deleted records from reappearing in WINS after
	subsequent replication with other servers. Where a WINS server is no longer
	active on the network, this is not a problem. For inactive owner servers, you
	can use tombstoning effectively from other active WINS servers to remove records
	owned by the inactive servers that are still present in WINS.
	
	The owner of a given WINS server record is typically the first server contacted
	by the WINS client during the registration process and the actual server first
	used to register the client's local names in WINS. In most cases, the WINS
	server that owns a client's name records in WINS will correspond to the primary
	WINS server as configured on the WINS client computer. Where the configured
	primary WINS server is not available during client registration, a configured
	secondary WINS server may be used instead to perform the actual registration of
	the client's names and become the owner. To verify the exact owner server for a
	WINS record, view owner information in the Show Database dialog box using WINS
	Manager.
	
	Tombstoning uses the following sequence of events to remove the selected records
	from all WINS servers that share and replicate the records to be tombstoned.
	
	1. The owner WINS server marks and changes the status of selected WINS records
	  from Active to Tombstoned in its local WINS server database.
	
	  WINS then treats the records as inactive and released from use. After these
	  records are tombstoned locally, the owner WINS server will not respond or
	  resolve NetBIOS name queries for these names from other WINS clients and WINS
	  servers unless the records are registered again by the WINS client.
	
	2. The owner WINS server replicates the selected records as tombstoned to other
	  WINS servers during subsequent replication cycles.
	
	  The records are not forcibly and immediately removed from WINS, but are
	  flagged or marked for eventual deletion. The exact replication cycle (or
	  Extinct Interval) is set in the server's WINS database properties. The
	  records are not removed from WINS data until the extinction interval has
	  actually expired. This allows other WINS servers to be notified that these
	  records are no longer in use, update their replicated mappings for these
	  records, and further replicate this updated WINS data to other servers.
	
	3. Records become extinct on all replicated WINS servers and are eventually
	  removed physically from all WINS servers.
	
	  After all WINS servers that participate in replication have completed a full
	  replication cycle and arrived at a consistent state, the tombstoned records
	  expire and are removed from each server's WINS database when it performs the
	  next database scavenging operation. After scavenging occurs on all servers,
	  the records no longer appear in WINS Manager and are no longer physically
	  stored in the WINS database.
	
	Multi-select Operations for WINS Database Records:
	
	WINS Manager now provides support for deletion or removal operations to multiple
	records in the Show Database dialog box. In previous versions of WINS Manager,
	only one record could be selected at a time.
	
	Burst Mode Handling for WINS Servers
	------------------------------------
	
	WINS servers can now support handling of high-volume, or burst server loads,
	where a large number of WINS clients actively seek to register their local names
	in WINS at the same time. With burst mode support, the WINS server can respond
	positively to clients that submit registration requests before it has processed
	and physically entered these updates in the WINS server database.
	
	Burst mode uses a burst queue size as a threshold value to determine how many
	name registration and name refresh requests sent by WINS clients will be
	processed normally before burst mode handling is started. By default, the burst
	queue is sized to allow 500 requests before burst handling is used.
	
	How Burst Handling Works
	------------------------
	
	Burst handling is enabled for any WINS server running under Windows NT Server 4.0
	with the current service pack update release applied. Where a WINS server
	supports burst handling, the server will initiate burst handling once the number
	of WINS client registration requests exceeds the burst queue size.
	
	Burst handling is used to temporarily achieve a steady and gradual registration
	state for the WINS server when the server is first started with a clean database
	or when many WINS clients come online for the first time. Either situation can
	cause a large amount of name registration and name refresh traffic to occur.
	
	For burst handling, additional client requests beyond the amount specified by the
	burst queue size are immediately answered with a positive success response by
	the WINS server. The response also includes a varied time-to- live (TTL) to
	clients to help regulate the client registration load and distribute processing
	of the requests over time.
	
	The purpose of using TTLs in the success responses is to slow the refresh and
	retry rate for new WINS clients and regulate the burst of WINS client traffic.
	For example, if the default burst queue size (500 entries) is used, the WINS
	server will reply immediately to the next 100 WINS client registration requests
	by sending early success responses that use a starting TTL value of 5 minutes.
	
	For each additional round of 100 client requests, the TTL is incremented by the
	WINS server to add 5 minutes (such as 10, 15, 20 minutes, and so on) until a
	maximum of 50 minutes is used as the response TTL value. If WINS client traffic
	is still arriving at bursted levels after the maximum TTL has been used to
	answer clients, the next round of 100 client requests will be answered starting
	over with the initial TTL value of 5 minutes and the entire process for
	incrementing the response TTL is repeated.
	
	This behavior will continue until the WINS server reaches its maximum intake
	level of 25,000 name registration and refresh queries. At this point, the WINS
	server will begin dropping queries.
	
	Configuring Burst Mode Support:
	
	You may use these additional registry values to further configure or disable
	burst mode support where desired.
	
	NOTE: By default, the following WINS registry values are not present and must be
	manually added to reconfigure or disable burst mode support on the WINS server.
	However, if you plan to use the default server behavior (which enables burst
	mode handling at the WINS server using a default burst queue size of 500
	entries), you will not need to add these Registry values or make any additional
	configuration changes to the WINS server.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" online Help topic in Registry Editor (Regedit.exe) or the "Add and
	Delete Information in the Registry" and "Edit Registry Data" online Help topics
	in Regedt32.exe. Note that you should back up the registry before you edit it.
	
	- BurstQueSize
	
	  You can add this registry value to adjust the maximum number of WINS client
	  request entries that will be queued at the WINS server before it begins using
	  burst handling.
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services
	  \Wins\Parameters\BurstQueSize
	
	  NOTE: The above registry key is one path; it has been wrapped For
	  readability.
	
	  Type:        REG_DWORD
	  Default:     500
	  Range:       Valid values are 50-5000
	
	  Description: Sets the maximum number of name registration and refresh queries
	  that are stored in the server's intake queue before burst handling is
	  activated by the WINS server. This value has no effect where burst handling
	  is disabled (for example, if the BurstHandling key has been added and set to
	  a value of 0).
	
	- BurstHandling
	
	  You can add this registry value to disable the use of burst mode handling by
	  the WINS server.
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Wins\Parameters
	  \BurstHandling
	
	  NOTE: The above registry key is one path; it has been wrapped for
	  readability.
	
	  Type:        REG_DWORD
	  Default:     1
	  Range:       0 (disabled) or 1 (enabled)
	
	  Description: This key determines whether the WINS server will use burst
	  handling to send success responses to the clients in the queue. If the value
	  of this entry is 0, the WINS server does not support burst handling or send
	  early success responses to WINS clients. If the value of this entry is 1, the
	  WINS server supports burst handling and sends early success responses to WINS
	  clients.
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbFEA kbWinNT400sp4fea 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400search kbWinNT400search kbWinNTW400sp4 kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp4 kbWinNTS400sp4 kbWinNTS400search
	Version           : :4.0 SP4
	Issue type        : kbinfo
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
