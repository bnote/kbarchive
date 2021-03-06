---
layout: page
title: "Q185587: Guide To Windows NT 4.0 Profiles and Policies (Part 2 of 6)"
permalink: /kb/185/Q185587/
---

## Q185587: Guide To Windows NT 4.0 Profiles and Policies (Part 2 of 6)

{% raw %}

	Article: Q185587
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 27-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article is the second in a series of articles that provides information and
	procedures for implementing Microsoft Windows NT 4.0 Profiles and Policies on
	client workstations and servers.
	
	A whitepaper is available that contains all of this information and additional
	flowcharts, diagrams and examples and can be downloaded from the following web
	page:
	
	  http://www.microsoft.com/ntserver/techresources/management/prof_policies.asp
	
	For the other sections of this guide, please see the following article(s) in the
	Microsoft Knowledge Base:
	
	  Q161334 Guide to Windows NT 4.0 Profiles & Policies Part 1 of 6
	
	  Q185588 Guide to Windows NT 4.0 Profiles & Policies Part 3 of 6
	
	  Q185589 Guide to Windows NT 4.0 Profiles & Policies Part 4 of 6
	
	  Q185590 Guide to Windows NT 4.0 Profiles & Policies Part 5 of 6
	
	  Q185591 Guide to Windows NT 4.0 Profiles & Policies Part 6 of 6
	
	MORE INFORMATION
	================
	
	                  Windows NT Server Operating System
	                            White Paper
	        Guide to Microsoft Windows NT 4.0 Profiles and Policies
	
	Copyright 1997 Microsoft Corporation. All rights reserved.
	
	The information contained in this document represents the current view of
	Microsoft Corporation on the issues discussed as of the date of
	publication. Because Microsoft must respond to changing market conditions,
	it should not be interpreted to be a commitment on the part of Microsoft,
	and Microsoft cannot guarantee the accuracy of any information presented
	after the date of publication.
	
	This White Paper is for informational purposes only. MICROSOFT MAKES NO
	WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.
	
	Microsoft, the BackOffice logo, MS-DOS, Windows, and Windows NT are
	registered trademarks of Microsoft Corporation.
	
	Other product or company names mentioned herein may be the trademarks of
	their respective owners.
	
	Microsoft Corporation
	One Microsoft Way
	Redmond, WA 98052-6399
	USA
	0997
	
	HOW USER PROFILES ARE HANDLED IN WINDOWS 95
	===========================================
	
	When a user logs on to a Windows 95 machine, the local profile path,
	HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Profile List,
	is checked for an existing entry for that user.
	
	If the user has an entry in this registry location, Windows 95 checks for a
	locally cached version of the user's profile. Windows 95 also checks the
	user's home directory (or other specified directory if the location has
	been modified) on the server for the User Profile. If a profile exists in
	both locations, the newer of the two is used. If the User Profile exists on
	the server, but does not exist on the local machine, the profile on the
	server is downloaded and used. If the User Profile only exists on the local
	machine, that copy is used.
	
	If a User Profile is not found in either location, the Default User Profile
	from the Windows 95 machine is used and is copied to a newly created folder
	for the logged on user. At log off, any changes that the user made are
	written to the user's local profile. If the user has a roaming profile, the
	changes are written to the user's profile on the server.
	
	USER PROFILE PLANNING AND IMPLEMENTATION
	========================================
	
	A successful implementation of User Profiles requires planning and
	preparation. Before creating User Profiles, consider the following:
	
	- How much of the user environment do you wish to control? Would System
	  Policies-either in conjunction with User Profiles, or by themselves-be a
	  better solution?
	
	- Will users be required to use a specific set of desktop folders and
	  environment settings?
	
	- Will users be able to make modifications to their profiles?
	
	- What features will you be implementing in User Profiles? Optional
	  features include persistent network connections, custom icons,
	  backgrounds, and so on.
	
	- For roaming profiles, will users be allowed to use the default profile
	  from the client workstation or will a standardized server-based default
	  profile be used instead?
	
	- Where will the profiles be stored, and is there enough drive space to
	  store them?
	
	- Where do existing user home directories reside?
	
	- How will shortcuts and links be displayed for the user?
	
	- What are the speeds of the links between the clients and the server
	  storing the profiles?
	
	These issues are examined more fully in the following paragraphs. For more
	information, refer to the Windows NT Server Concepts and Planning Guide.
	
	SETTING PERMISSIONS FOR USER PROFILES
	=====================================
	
	When troubleshooting or preparing for a rollout of User Profiles, you
	should pay careful attention to permissions at the Windows NT File System
	(NTFS) and share levels. If the profile is mandatory, the user account
	should have at least Read permissions on the network share where that
	user's User Profile is stored. If the user's profile is roaming, the user
	must have Change permissions (or better) because the client will need to
	write the changes back to the central profile on the shared network drive
	when the user logs off. If roaming profiles are stored on an NTFS
	partition, you can choose to remove the Delete permission from the default
	Change permissions at the NTFS level.
	
	NOTE: Directories containing roaming User Profiles need at least Add and
	Read permissions for profiles to be read correctly. If you use Add
	permissions only, when Windows NT checks for the existence of the profile
	it will fail because it looks for the path first, and if Read rights are
	not given, the check will fail.
	
	Permissions are also important on a client machine where the user is
	logging on interactively. If Windows NT is installed in an NTFS partition
	on the client computer, and the user does not have at least the default
	permissions as outlined in the Windows NT Server Concepts and Planning
	Guide (page 132), errors can occur. For example, if permissions are
	incorrect on the root of the system directory, the following message
	appears: "Can't access this folder-the path is too long." A blank desktop
	is displayed, and the user's only option is to log off.
	
	If permissions are set incorrectly in the %systemroot%,
	%systemroot%\System, %systemroot%\System32, or %systemroot%\System32\Config
	directories, the following message appears: "Unable to log you on because
	your profile could not be loaded."
	
	ENCODING PERMISSIONS IN THE USER PROFILE
	========================================
	
	The registry portion of the User Profile, Ntuser.xxx, is encoded with the
	user or group that has permission to use that profile. Once this is saved,
	you can use the Registry Editor to modify this information if you want to
	change the permissions on a profile without replacing it.
	To change encoded User Profile information:
	
	1. Follow the instructions to manually edit a profile: (Refer to the
	  section "Administering a User Profile Manually through the Registry"
	  later in this document).
	
	2. Change the permissions on the root of the key to include users and
	  groups who will have permission to use the profile.
	
	3. Unload the hive.
	
	SELECTING A LOCATION TO SAVE USER PROFILES
	==========================================
	
	As with Windows NT 3.5x, you can place a roaming profile in any shared
	directory, and then configure the user account profile path to point to the
	profile. The Profiles directory in the system root stores local User
	Profiles, "All Users" profile settings (which apply to any user who uses
	the computer), the "Default User" profile, and cached User Profiles of
	domain users. You should avoid using the %systemroot%\Profiles directory in
	the domain users' profile path as a location to store server-based
	profiles, whether they are roaming or mandatory. (The path should allow the
	user's profile to roam with the user and be available on any networked
	computer that the user logs on to. If you specify a path to the
	%systemroot%\Profiles directory, the client computer always uses the local
	profile instead.)
	
	Windows NT 4.0 profiles can be saved on any Windows NT 3.5x or 4.0 server
	because the client computer uses the path where the profile is stored only
	as a location to download the profile and to write the modified user
	profile at log off. This allows profiles to be stored on any shared network
	drive. The process of downloading the profile is controlled by the client
	computer-all the client needs is the correct path. Note that storing
	profiles on a Windows NT 4.0 Server makes it easier for the administrator
	to open a user's Ntuser.dat file to make any necessary modifications. You
	can also store User Profiles on Novell Servers provided that the client is
	configured correctly and can access the profile path.
	
	If a client is not receiving a User Profile at logon, use the Start menu
	Run command to check the profile path. For example, to see if you can
	locate the profile, type \\server\share\mydomainuser. If the path to the
	user's profile contains spaces, put quotation marks around the path when
	you type it in the Run command box.
	
	Except in the case of mandatory profiles or when a slow network is
	detected, any changes to the user's profile are saved to the central
	profile when the user logs off. (Because users cannot modify mandatory
	profiles, changes do not need to be written to the server.)
	
	NOTE: In situations where the same user account logs on to multiple
	machines, the last user to log off dictates the profile settings because
	that user was the last one to write data to the profile. Similarly, if a
	group of users all point to the same profile, the final logoff settings are
	saved and will overwrite previous settings.
	
	If the User Profile is flagged as a local profile and is not mandatory, any
	changes the user makes while logged on are written to the locally cached
	version of the profile, but not to the server-based copy.
	
	NOTE: You should not make the home directory and User Profile path the
	same. If the profile path encompasses the home directory path and the
	server-based profile is more recent than the local profile on the
	workstation, all directories and files that exist in the user's home
	directory will be copied to the user's workstation at logon. These files
	are then written back to the server (if modified) when the user logs off.
	This process occurs at each logon. In addition, even if the user logs off
	and the administrator deletes all of the unnecessary files from the home
	directory, the versions of these files that reside on the workstation will
	not be deleted at logon and will be written back to the server again at log
	off. This file copy process is avoided if you place the profile in a
	subdirectory of the home directory, as follows:
	\\server\share\domainuser\profile.
	
	SETTING PERSISTENT CONNECTIONS
	==============================
	
	Persistent connections are stored in the User Profiles registry hive under
	the Network subkey. If you create a template User Profile that includes
	persistent connections and you have to supply credentials when making those
	connections, the credentials-with the exception of the password you used-
	are stored in the User Profile. When the new user receives the template
	User Profile, these saved credentials are passed (as opposed to the logged
	on user's credentials), and the connection may fail.
	
	There are three methods to correct this:
	
	1. You can recreate the profile without supplying alternate credentials
	  when connecting to network resources, or
	
	2. Using Registry Editor (Regedt32.exe), use blank spaces to erase the
	  contents of the USERNAME value under HKEY_CURRENT_USER\Network\drive
	  letter. (Do not delete the value-just fill it with blank spaces.) Save
	  the profile. For additional help, refer to the section "Administering a
	  User Profile Manually Through the Registry" later in this document, or
	
	3. Delete the network connection and reconnect.
	
	WORKING AROUND SLOW NETWORK LINKS
	=================================
	
	Slow Net (which is configured in System Policy) was designed to offer a
	user faster access to his or her User Profile if the system detects a
	slower network speed, such as a modem line connection. Instead of
	automatically downloading a profile that may be several hundred kilobytes
	to several megabytes large, Slow Net gives the user the option of either
	downloading the profile or using the locally cached version. If the cached
	file is used, it can significantly reduce the time it takes to log on to
	the computer. To detect a slow network, the operating system computes the
	amount of time it takes to receive a response from the server (which the
	profile path defines as part of the user account). As system administrator,
	you can determine the allowable slow network speed. Use the System Policy
	Editor to set this value.
	
	If the user uses the Control Panel System application to change the profile
	type to Local, then the cached copy of the User Profile is opened every
	time the user logs on. Any changes that occur to the profile are written
	locally and not to the server location.
	
	CREATING AND MAINTAINING USER PROFILES
	======================================
	
	Creating a New Roaming User Profile for Windows NT 4.0
	------------------------------------------------------
	
	To create a new roaming User Profile, you must first determine where the
	user's profile will be stored. You then must create a user account (if one
	doesn't already exist), and specify a User Profile path. Finally, you must
	specify whether a given user will use a specific profile or can use a
	default profile. These procedures are described below.
	
	To create a new roaming user profile:
	
	1. If a location has not already been prepared, create a directory on the
	  server and establish a network share. Give the user a minimum of Change
	  permissions to the shared directory. (For more information on planning
	  for this type of user, read the sections "Selecting a Location to Save
	  User Profiles" and "Setting Permissions for User Profiles" earlier in
	  this document.) If your implementation stores user profiles within
	  users' home directories, make the profile directory a subdirectory of
	  the user's home directory. (Note that this approach precludes the use of
	  the %USERNAME% variable.) To prevent the share from being browsable,
	  append "$" to the share name.
	
	2. If this will be a domain user or if this will be a local account for a
	  Windows NT Server-based machine, use User Manager for Domains to create
	  the account. If this will be a Windows NT 4.0 Workstation account, use
	  the version of User Manager included in the Administrative Tools program
	  group. Refer to your operating system documentation and online Help for
	  procedures when using these tools. (Note that for this example, the user
	  account is mydomainuser.)
	
	3. Enter the User Profile path. This is the location where the User Profile
	  will be stored, for example: \\myserver\myshare\mydomainuser. Or, if the
	  profile is being stored within the user's home directory, use:
	  \\myserver\myshare\MyUsersHomeDir\profile.
	
	4. If the user is to receive the Default User profile from the workstation
	  where he or she will interactively log on, no further administration is
	  required.
	
	  If the user's profile will be a copy of an existing user profile, refer
	  to Step 9. Otherwise, use User Manager to create an account for
	  establishing a template profile. So that you can easily identify this
	  account, we recommend that it be called TemplateUser.
	
	5. Using the template account (TemplateUser), log on to the local machine
	  or domain. A new directory with the same name as the user name created
	  in Step 4 will be created in the %systemroot%\Profiles directory when
	  you first log on. For example, if the user name is TemplateUser, the
	  resulting directory name will be %systemroot%\Profiles\TemplateUser.
	
	6. Modify any items that need to differ from the current default (for
	  example, you may choose to modify the background color or bitmap,
	  shortcuts on the desktop, and View options in My Computer).
	
	7. Log off, and then log back on to the same computer using an account with
	  administrative privileges.
	
	8. Place the template profile in the appropriate location for the type of
	  profile distribution that will be used. (The template profile, including
	  customizations, is stored initially in
	  %systemroot%\Profiles\TemplateUser.)
	
	   - If the template profile will be distributed manually to multiple
	     users:
	
	     a. Create a directory where the template profile will be stored for
	        distribution to each user account created.
	
	     b. From the Windows NT-based machine hosting the template profile to
	        be used, log on as an administrator.
	
	     c. From the Control Panel, click System. From the User Profiles page,
	        use the Copy To option to enter the path of the directory you just
	        created.
	
	     d. Modify the permissions to allow the Everyone group to use the
	        profile. To do this, click the Change button, select the group,
	        and click OK.
	
	     e. Continue to Step 9.
	
	   - If the template profile will be distributed via the Default User
	     folder on validating servers:
	
	     a. Create a Default User directory in the NETLOGON share (which is
	        %systemroot%\Repl\Import\Scripts by default) of validating domain
	        controllers. This folder name must be named Default User or the
	        profile will not be downloaded from the server. To keep the
	        Default User profile consistent across domain controllers and to
	        ease administrative overhead, you can create this folder on one
	        computer and then use the directory replication service to export
	        it to all validating domain controllers.
	
	     b. If a user logs on and does not have an existing local or server-
	        based profile and your implementation uses the Default User folder
	        on validating domain controllers, Windows NT will check the
	        NETLOGON share for the Default User profile before it uses the
	        local default profile. (Workstations save the server Default User
	        profile on a local cache.) Windows NT will check the
	        time/date/size of the server copy against the locally cached copy
	        before downloading the server copy. And, if the files are
	        identical, Windows NT will use the local copy of the server
	        Default User profile.
	
	     c. Continue to Step 10.
	
	9. In the \\server\share from Step 1, create the directory structure you
	  specified as the path in Step 3. For example, create the directory
	  mydomainuser under \\myserver\myshare. If the profile is to be stored
	  within the user's home directory, use the directory structure
	  \mydomainuser\profile under \\myserver\myshare.
	
	10. Copy the profile appropriate to your implementation.
	
	    - To copy an existing user's profile to another user:
	
	      a. From the Windows NT-based machine hosting the profile to be used,
	         log on as an administrator.
	
	      b. From the Control Panel, click System. On the User Profiles page,
	         select the profile to be copied and use the Copy To option to
	         enter the path of the directory you created in Step 9.
	
	      c. Modify the permissions to reflect the proper account. To do this,
	         click the Change button, select the account, and click OK. Click
	         OK again to copy the profile.
	
	    - To copy the template profile to the Default User folder on
	      validating domain controllers:
	
	      a. From the Windows NT-based machine hosting the profile to be used,
	         log on as an administrator.
	
	      b. From the Control Panel, click System. On the User Profiles page,
	         select the profile to be copied and use the Copy To option to
	         enter the path of the Default User directory on the validating
	         domain controller.
	
	      c. Modify the permissions to reflect the Everyone group. To do this,
	         click the Change button, select the account, and click OK. Click
	         OK again to copy the profile.
	
	    - To copy a template profile manually to a number of users:
	
	      a. Copy the entire contents (files and subdirectories) from the
	         directory containing the template user profile created in Step 8
	         to the directory created in Step 9.
	
	      b. Repeat this for each of the user profile directories that will
	         receive the template user profile.
	
	NOTES:
	- When entering the path to the target directory, you can use Uniform
	  Naming Convention (UNC) names. However, if you are going to use the
	  Browse function to locate the target directory for the profile, it is
	  important that you first map a drive to the \\server\share where the
	  profile will be stored.
	- The mydomainuser name shown in Step 2 does not have to be the user's
	  name. Many user accounts or groups can be configured to point to the
	  same profile. Of course, if the profile is shared by a group of users
	  and is not mandatory, as each user logs off, the user's changes are
	  written back to the shared profile.
	- The profile does not need to be stored one directory below the
	  server\share. The profile can be nested several directories below, or
	  the profile path can be local.
	- If the profile path points to a directory on the local machine, a share
	  is not needed.
	- The variable %USERNAME% is replaced by the user name only once in the
	  User Profile path in User Manager, and it must be the last subdirectory
	  in the path. However, extensions can still be added, such as .usr or
	  .man.
	- You can select any group or a specific user when setting the
	  permissions. However, only the user or group specified will be able to
	  use the profile. For this reason, it is recommended that the Everyone
	  group be given permission to use template profiles.
	
	Once the above steps are completed, the user receives the appropriate
	profile as follows:
	
	- If the user is to receive the Default User profile from a Windows NT
	  4.0-based workstation, the workstation's default profile is used when
	  the user first logs on. When the user logs off, the profile is
	  automatically written to the local cache and to the server-based
	  profile.
	
	- If the user is to receive the Default User profile from the validating
	  domain controller, the default profile from the server is used when the
	  user first logs on. When the user logs off, this profile is
	  automatically written to the local cache and to the server-based
	  profile.
	
	- In all other cases, the profile-including the folder trees and the
	  Ntuser.xxx file originally included with the profile-is written to the
	  user's profile directory. The permissions are also encoded into the
	  binary Ntuser.xxx file.
	
	Creating a New Mandatory User Profile for Windows NT 4.0
	--------------------------------------------------------
	
	To create a new mandatory User Profile:
	
	1. If a location has not already been prepared, create a directory on the
	  server and establish a network share. Users who will have mandatory
	  profiles need only Read permissions to the shared directory. (For more
	  information on planning for this type of user, read the sections
	  "Selecting a Location to Save User Profiles" and "Setting Permissions
	  for User Profiles" earlier in this document.) If your implementation
	  stores user profiles within users' home directories, make the profile
	  directory a subdirectory of the user's home directory. (Note that this
	  approach precludes the use of the %USERNAME% variable.) To prevent the
	  share from being browsable, append "$" to the share name.
	
	2. If this will be a domain user or if this will be a local account for a
	  Windows NT Server, use User Manager for Domains to create the account.
	  If this will be a Windows NT 4.0 Workstation account, use the version of
	  User Manager included in the Administrative Tools program group. Refer
	  to your operating system documentation and online Help for procedures
	  when using these tools. (Note that for this example, the user account is
	  mydomainuser.)
	
	3. Enter the User Profile path. This is the location where the User Profile
	  will be stored, for example: \\myserver\myshare\mydomainuser. Or, if the
	  profile is being stored within the user's home directory, use:
	  \\myserver\myshare\MyUsersHomeDir\profile.
	
	4. Determine if an extension needs to be appended to the User Profile path.
	  If it will be mandatory that the user reads the profile from the server,
	  and if logon will be denied unless this is the case, add the extension
	  .man to the User Profile path; for example:
	  \\myserver\myshare\mydomainuser.man.
	
	5. Use User Manager to create an account for establishing the template
	  profile. So that you can easily identify this account, we recommend that
	  it be called TemplateUser.
	
	6. Using the template account (TemplateUser), log on to the local machine
	  or domain. A new directory with the same name as the user name created
	  in Step 2 will be created in the %systemroot%\Profiles directory when
	  you first log on. For example, if the user name is TemplateUser, the
	  resulting directory name will be %systemroot%\Profiles\TemplateUser.
	
	7. Modify any items that need to differ from the current default (for
	  example, you may choose to modify the background color or bitmap,
	  shortcuts on the desktop, and View options in My Computer).
	
	8. Log off, and then log back on to the same computer using an account with
	  administrative privileges.
	
	9. In the \\server\share from Step 1, create the directory structure you
	  specified as the path in Step 3. For example, you would need to create
	  the directory mydomainuser under \\myserver\myshare. Or, if the profile
	  is stored in the user's home directory, you would need to create the
	  directory structure \mydomainuser\profile under \\myserver\myshare.
	
	  If you appended the .man extension to the User Profile path in Step 4,
	  append the .man suffix to the directory name for the folder where the
	  profile will be stored. The .man extension identifies a Windows NT 4.0
	  mandatory profile that must be accessible for the user to logon. For
	  example, if the user name is mydomainuser, the path to the mandatory
	  profile would be \\myserver\myshare\mydomainuser.man.
	
	  If you also have a mandatory Windows NT 3.5x profile for the user, use
	  the .pdm extension in place of the .man extension (for example,
	  \\myserver\myshare\mydomainuser.pdm). The .pdm extension is required
	  because the profile folder cannot have the same name as the Windows NT
	  3.5x User Profile located in the same parent folder.
	
	10. From the Windows NT-based machine hosting the template profile to be
	   used, log on as an administrator.
	
	11. From the Control Panel, click System. From the User Profiles page,
	   select the profile to be copied and use the Copy To option to enter the
	   path of the directory you created in Step 9.
	
	12. Modify the permissions to allow the user or group to use the profile.
	   To do this, click the Change button, select the account, and click OK.
	   You can select any group or specific user when setting the permissions;
	   however only the user or group specified will be able to use the
	   profile.
	
	   The profile-including the folder trees and the Ntuser.xxx file
	   originally included with the profile-is written to the location you
	   designated. The permissions are also encoded into the binary Ntuser.xxx
	   file.
	
	13. In the directory that the profile was copied to in Step 3, check the
	   Ntuser.xxx file for the .man extension. If the extension is .dat, the
	   profile will still be modifiable. Change the extension to .man if
	   necessary.
	
	NOTES:
	- When entering the path to the target directory, you can use universal
	  naming convention (UNC) names. However, if you are going to use the
	  Browse function to locate the target directory for the profile, it is
	  important that you first map a drive to the \\server\share where the
	  profile will be stored.
	- The mydomainuser name shown in Step 2 does not have to be the user's
	  name. Many user accounts or groups can be configured to point to the
	  same profile. Because this is a mandatory profile, this may be the
	  desired use of the profile since the administrator wants all the users
	  in the group to receive the same settings.
	- The profile does not need to be stored one directory below the
	  \\server\share. The profile can be nested several directories below, or
	  the profile path can be local.
	- If the profile path points to a directory on the local machine, a share
	  is not needed.
	- The variable %USERNAME% is replaced by the user name only once in the
	  User Profile path, in User Manager, and it must be the last subdirectory
	  in the path. However, extensions can still be added, such as .usr or
	  .man.
	- The %LOGONSERVER% variable can be used for mandatory profiles to provide
	  fault tolerance. Do not place double slashes ( \\) in front of
	  %LOGONSERVER%; doing so will prevent the variable from being read
	  properly. See Microsoft Knowledge Base article Q141714 for more
	  information.
	- You can use the TemplateUser account to test changes before making them
	  available to users by copying the adjusted profile directory to test
	  accounts prior to rollout.
	- You can select any group or a specific user when setting the
	  permissions. However, only the user or group specified will be able to
	  use the profile. For this reason, it is recommended that the Everyone
	  group be given permission to use template profiles.
	
	Making a Roaming Profile Mandatory in Windows NT 4.0
	----------------------------------------------------
	
	You have two options when configuring a mandatory roaming profile: you can
	change the user's ability to modify the User Profile, or you can change the
	user's ability to modify the User Profile and enforce the use of the server-
	based profile at logon. With the second option, the user is not able to log
	on to the system if the network profile is unavailable. Each of these
	procedures will be explained more fully below.
	
	Changing the User's Ability to Modify a Profile
	-----------------------------------------------
	
	When creating a User Profile or at any time thereafter, you have the option
	of enforcing whether or not the user can modify the profile by changing the
	extension on the Ntuser.dat file. The Ntuser.dat file is located in the
	root of the user's profile directory. If you change the name of this file
	to Ntuser.man, when Windows NT reads the profile, it marks the profile as
	read-only, and any changes that the user makes while logged on are not
	written back to the server-based profile when he or she logs off.
	
	To change the user's ability to make modifications to the User Profile:
	
	1. Locate the user's profile in the account's User Profile path.
	
	2. While the user is logged off, rename the Ntuser.dat file to Ntuser.man.
	  (Note that if you make this change while the user is logged on, the
	  user's copy of the profile will overwrite your changes, because at the
	  time the user logged on, he or she had permission to overwrite the
	  profile.)
	
	Be cautious if you use the Windows NT Explorer interface to make these
	changes. If you have the "Hide file extensions for known file types" option
	enabled (this is the default), be sure to check the properties to be sure
	that there are not two extensions. For example, say you want to make a
	profile mandatory and you use Explorer to rename the Ntuser.dat file name
	to Ntuser.man. Because of the Hide extensions default, Explorer saves the
	file as type .man, but does not display the .man extension. Later, you
	decide to allow the user to make changes again, and through Explorer, you
	rename the file back to Ntuser.dat. However, because Explorer was hiding
	that part of the file name that determines its type, the only thing you
	
	rename is the prefix. The file name is now Ntuser.dat.man. To avoid this
	situation, you can either rename files from the command line or change the
	behavior of Explorer.
	
	Enforcing the Use of the Server-based Profile
	---------------------------------------------
	
	In addition to enforcing the read-only property of a profile, the
	administrator can duplicate the functionality that was available in Windows
	NT 3.5x of not allowing the user to log on unless the server profile is
	available.
	
	To enforce the use of the server-based profile for a given user:
	
	1. Append the .man extension to the User Profile path in User Manager as
	  explained in the previous section. (Skip this step for users who have
	  existing Windows NT 3.5x profiles and who already have the .man
	  extension appended to their profile paths.)
	
	2. If the user already has a Windows NT 3.5x mandatory profile on the
	  server, change the name of the folder where the Windows NT 4.0 roaming
	  profile currently exists to foldername.pdm. If the user logs on to a
	  Windows NT 4.0-based workstation and the User Profile path contains the
	  .man extension, Windows NT will determine that a mandatory Windows NT
	  3.5x profile exists and will automatically replace the .man extension
	  with .pdm and will look for the directory path configured in the User
	  Profile path. For example, at logon if the User Profile path is
	  configured to use \\server\share\username.man, Windows NT will look for
	  \\server\share\username.pdm for the correct profile to load.
	
	  If only the Windows NT 4.0 user profile exists, change the name of the
	  folder where the Windows NT 4.0 roaming profile exists to
	  foldername.man. If the user logs on to a Windows NT 4.0-based
	  workstation and the User Profile path contains the extension .man,
	  Windows NT will look for the directory path configured in the User
	  Profile path. If Windows NT does not find the directory, it will replace
	  the .man extension with .pdm, and will check again.
	
	3. If you haven't already done so, change the name of the Ntuser.xxx file
	  to Ntuser.dat. (Refer to the section, "Changing the User's Ability to
	  Modify a Profile, " in this document.)
	
	Creating a New Roaming User Profile for a Windows 95 User
	---------------------------------------------------------
	
	If you have Windows 95 users in your domain, you can create roaming user
	profiles for them as well.
	
	To create a roaming user profile for a Windows 95 user:
	
	1. On the client Windows 95-based computer, start Control Panel, and select
	  Passwords.
	
	2. From the User Profiles property page, enable the option that allows
	  users to have individual profiles, and set the Primary Network Logon to
	  Client for Microsoft Networks.
	
	3. Reboot the client machine.
	
	4. Use User Manager for Domains to create the user account (if it does not
	  already exist). For the user's home directory, specify the location
	  where the User Profile will be stored. An example would be:  <image
	  present in whitepaper>
	
	  This automatically creates a folder with the user name. If a dialog box
	  is displayed stating that the operation failed, create the folder
	  manually before continuing.
	
	5. Decide whether the user will receive a specific profile or if a default
	  will be used instead:
	
	   - If the user will receive a specific profile, from the Windows 95-
	     based computer hosting the profile to be used, copy the complete
	     contents of the local Profile folder to the folder created in Step 4.
	     This writes the profile to the destination, including the folder
	     trees and the User.xxx file originally included with the profile.
	
	   - If a default profile will be used, no administrative action is
	     required. When the user logs on, the Default User Profile from the
	     local Windows 95-based machine will be used. At log off, this profile
	     will be written to the user's home directory with any customizations
	     the user has made.
	
	NOTES:
	- If you need to troubleshoot problems with users not receiving their User
	  Profiles, have the users execute the command: NET USE * /HOME from the
	  command prompt on the client machine. This verifies that the user can
	  access the home directory, and allows the user to verify that the User
	  Profile exists in that folder.
	- The profile does not need to be stored one directory below the
	  \\server\share. The profile can be nested several directories below, if
	  desired.
	
	Creating a New Mandatory User Profile for Windows 95
	----------------------------------------------------
	
	If you have Windows 95 users in your domain, you can create new mandatory
	user profiles.
	
	To create a mandatory user profile for a Windows 95 user:
	
	1. On the client Windows 95-based computer, start Control Panel, and select
	  Passwords.
	
	2. From the User Profiles property page, enable the option that allows
	  users to have individual profiles, and set the Primary Network Logon to
	  Client for Microsoft Networks.
	
	3. Reboot the client machine.
	
	4. Use User Manager for Domains to create the user account (if it does not
	  already exist). For the user's home directory, specify the location
	  where the User Profile will be stored. An example would be:  <image
	  present in whitepaper>
	
	  This automatically creates a folder with the user name. If a dialog is
	  displayed stating that the operation failed, create the folder manually
	  before continuing.
	
	5. Copy the Template Profile that you are using for mandatory profiles to
	  the user's home directory:
	
	   - From the Windows 95-based machine hosting the mandatory, copy the
	     complete contents of the local Profile folder to the folder created
	     previously. This writes the profile to the destination, including the
	     folder trees and the User.xxx file originally included with the
	     profile.
	
	   - If you have not already done so, rename the User.dat file to
	     User.man.
	
	At logon, the user will download the mandatory profile, cache it, and no
	changes will be written back to the server at log off.
	
	NOTES:
	- The profile does not need to be stored one directory below the
	  \\server\share. The profile can be nested several directories below, if
	  desired.
	- Alternatively, a new profile can be made mandatory by the user logging
	  on, logging off, and the administrator changing the User.dat file to
	  User.man.
	
	Maintaining User Profiles with Control Panel System Properties
	--------------------------------------------------------------
	
	In Windows NT 4.0, much of the functionality provided by individual tools
	in Windows NT 3.5x has been consolidated in the Control Panel System
	Properties application. And System Properties, when used in conjunction
	with the System Policy Editor, provides even greater functionality than
	Windows NT 3.5x delivered. Some of the features of System Properties are
	described next.
	
	NOTE: In Windows NT 3.5x, you used the User Profile Editor to modify User
	Profile properties. In Windows NT 4.0, this tool has been replaced by a
	combination of the User Profile structure and System Policies. User Profile
	Editor is not included in the Windows NT 4.0 package.
	
	The User Profiles property sheet (shown in the figure below) allows you to
	view the list of User Profiles. From there you can delete, copy, or modify
	the profile type for each of the profiles listed. Note that the profiles
	listed are only for those users who have interactively logged onto the
	local machine. User profiles that have been created and not used or
	profiles that are stored for use on remote machines are not included in
	this list. Furthermore, if a user does not have administrative rights, only
	that user's profile is listed. Administrators have permissions to see all
	available profiles.
	
	Deleting Profiles
	-----------------
	
	The User Profiles property sheet allows users with administrator privileges
	to delete unused profiles that still exist on a local computer. (In Windows
	NT 3.5x, this function was available in the Main group of the Windows NT
	Setup program.) To delete a User Profile, select the profile name and click
	the Delete button. This deletes the User Profile on the local machine, but
	it does not delete the associated User Account. Note that sometimes the
	phrase "Account Deleted" is present in the list of profiles. These are
	accounts that were deleted from the User Account Database, but whose
	profiles still exist on the local computer.
	
	If you need to delete profiles on remote computers, the Delprof.exe utility
	available in the Windows NT Server Resource Kit, version 4.0, provides this
	functionality. Windows NT 4.0 User Profiles can grow quite large and can
	take up considerable disk space, particularly if several people are using
	one computer. With Delprof.exe, you can reclaim disk space by removing
	profiles that are no longer needed. This utility deletes User Profiles on
	computers running Windows NT, and it can be used on a local or remote
	computer running Windows NT 4.0 or earlier. However, because Delprof.exe is
	Unicode-based, it cannot run on Windows 95.
	
	NOTE: Delprof.exe will delete everything contained in a user's profile,
	including settings, colors, and user documents. Please be aware of any user
	documents that may be deleted before using this tool.
	
	The syntax of Delprof.exe is as follows:
	
	  delprof [/q] [/i] [/p] [/c:\\computername] [/d:days] [/?]
	
	Where:
	  /q  Runs Delprof.exe in quiet mode, with no confirmation for each
	      profile to be deleted.
	  /I  Indicates that Delprof.exe should ignore errors and continue
	      deleting.
	  /p  Prompts for confirmation before deleting each profile.
	  /c:\\computername  Specifies a remote computer name on which to run
	      Delprof.exe.
	  /d:days  Specifies the number of days of inactivity (days is an
	      integer). Profiles with longer inactivity will be deleted.
	  /?  Displays command-line syntax.
	
	See the Windows NT Server Resource Kit for more information.
	
	It is important to note that if a user is logged on locally to a machine
	and then attempts to delete his or her own profile, a message will appear
	stating that the profile is currently in use and cannot be deleted. The
	user must log off, log back on using a different account with administrator
	privileges, and delete the profile. In addition, if a service is running
	for a particular user account, the same message may appear. If this
	happens, stop the service and then delete the profile.
	
	Changing the Profile Type from Roaming to Local
	-----------------------------------------------
	
	With the User Profiles Change Type feature, a user can control which copy
	of the User Profile (local or roaming) is read when he or she logs on.
	(Note that the user can do this interactively while logged on.) Users do
	not need administrative privileges to change which profile is used if the
	profile is not a mandatory profile.
	
	Valid profile types are:
	
	- Local Profile-A local profile is maintained on the local computer. This
	  option allows the user to specify that the once "roaming" profile is now
	  "local" to this machine. Although the remote profile is still available,
	  if the Local Profile option is selected, the locally cached profile will
	  be used instead. The user should be aware that if he or she makes
	  changes to the profile, those changes will be saved in the locally
	  cached version only and will not be replicated in the server-based
	  profile. Note that the system can choose this selection automatically if
	  the server-based profile is unavailable.
	
	- Roaming Profile-If the user selects the roaming profile and the roaming
	  profile is available, Windows NT determines whether the server or local
	  copy is newer. If the local copy is newer, the user is asked to choose
	  which copy he or she would like to use. Note that if the system detects
	  a slow network link, the user will be given this same choice of
	  profiles. The Roaming Profile selection is available if:
	
	  1. There is a valid path specified in the User Profile path portion of
	     the user account properties, and
	
	  2. The User Profile path is accessible at the time of logon.
	
	- Roaming Profile with "Use cached profile on slow connections"-If a user
	  selects this option, he or she is not asked which copy to use with a
	  slow connection. Instead, the system uses the locally cached copy
	  automatically.
	
	If a user has a roaming profile, it is possible for that user to change the
	mode to Local and have Windows NT use the local version always, even though
	the roaming profile is still available. However, a user cannot do this if
	the system administrator assigns that user a mandatory profile and has
	added the .man extension to the user's profile path.
	
	Determining Which Profile Is Displayed
	--------------------------------------
	
	There may be cases where users who have identical names but are from
	different domains will log on to the same machine. If this occurs, you will
	notice several directories that start with the same prefix in the
	%systemroot%\Profiles directory tree. You can use the User Profiles
	property page to determine which file is associated with which user, as
	follows:
	
	1. Compare the Modified and Size properties to those of the actual
	  directories. The Size property displayed in User Profiles is the total
	  size of the directory residing in the profiles tree, not the size of the
	  Ntuser.xxx file alone. Match the directory sizes in the profiles tree to
	  the number displayed on the User Profiles property page.
	
	2. If the user is currently logged on, right-click the Start button. If
	  context menus have not been disabled, select the option to Explore and
	  Explorer will open to the profile directory used by that account.
	
	3. If you don't know when the user last logged on, look for the Ntuser.dat
	  file with a time and date stamp that matches the Modified date displayed
	  in the User Profiles property page.
	
	Copying Profiles
	----------------
	
	Use the User Profiles Copy To button to copy existing profiles from the
	local machine to another profile directory on the same machine or to a
	remote server where server-based User Profiles are stored. The Copy To
	dialog box (see the figure below) performs two functions. First, the Copy
	profile to option provides a Browse button that enables you to view local
	and remote drives to select the directory where the profile should be
	copied. In addition, the dialog provides a Permitted to Use option that
	allows you to select the user account or group that has permission to use
	the profile.
	
	When the permissions are written to the profile, they are stored in the
	Ntuser.xxx file. When a new profile is created, the user that created the
	profile is given permission to use that profile. However, those with
	administrator permissions can use the Change button or the Registry Editor
	to change these permissions.
	
	When you click the Browse button, the following dialog box appears (image
	present in whitepaper). It is important to note that this dialog does not
	allow you to create directories. You must create the required directories
	before you copy the profile.
	
	Viewing the Contents of the Profiles Directory on a Local Computer
	------------------------------------------------------------------
	
	All locally cached versions of User Profiles are stored in the profiles
	subdirectory of the Windows NT root directory. The profiles subdirectory
	maintains each user's profile separately by generating a specific directory
	for each user. Within that directory, the registry hive, Ntuser.dat, and
	the rest of the profile structure folders are kept. If a user is allowed to
	view context menus or has administrator privileges, the user can right-
	click the Start button, click the Explore option, and have the Explorer
	window automatically open to his or her profile directory with the contents
	displayed. In addition, administrators can click the Explore All Users
	option to display the All Users profile directory.
	
	You may notice that in a given user's profile directory, there are more
	files and directories than those listed in the example above. This may be
	due to the files and directories created by the user. For example, when the
	user logs on, if the server-based profile is found to be more recent than
	the one on the local computer, the entire contents of the User Profile path
	is copied to the client workstation and is then written back to the server
	when the user logs off. If the user has saved any documents in the home
	directory and the home directory is in the user's User Profile path, the
	documents become part of the User Profile. These documents are downloaded
	when you log on to the network and written back to the server when you log
	off the network. Note that this process could slow down the logon process
	considerably.
	
	Log Files Used by Profiles
	--------------------------
	
	Log files are binary files that track changes to a profile. As changes are
	made, they are recorded in a log file and then written to NTuser.xxx. If
	for some reason, the changes cannot be recorded in NTuser.xxx, they are
	applied at the next logon. When a user makes a change to his or her
	profile, the change is made to the user's locally cached profile, even if a
	mandatory profile is in use. (In this case, the changes are not propagated
	to the server copy and are overwritten the next time the user logs on.) If
	the user has a roaming User Profile, when the user logs off, the NTuser.dat
	file is copied to the server and the changes are saved (unless the profile
	is being used in a local mode).
	
	The All Users Shared Profile
	----------------------------
	
	The All Users profile directory contains common groups that apply to all
	users logging on locally to a given workstation. When a user logs on,
	programs and shortcuts from the All Users profile are also available to the
	user-in addition to the user's personal User Profile programs and
	shortcuts. Note that the All Users profile on a domain controller does not
	apply to domain users logging on at remote workstations. The All Users
	profile is workstation-specific and contains the common groups for just
	that computer. If you want to specify programs, shortcuts, or directories
	to be used by everyone who logs on to a specific workstation, you should
	place these in the All Users profile directory.
	
	If you need to establish domain-wide common groups and settings, use the
	System Policy Editor to modify registry entries on remote workstations so
	that they point to server directories for common groups, as opposed to
	pointing to the local All Users profile. Later, if you need to remove the
	domain-wide settings and have remote users point to the All Users profile
	from the local workstations once again, you'll need to change the default
	path used in the System Policy Editor to:
	
	  %systemroot%\Profiles\All Users\Start Menu\Programs
	
	Refer to the System Policy portion of this guide for specific procedures.
	
	Additional query words: wpaper
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWin95search kbZNotKeyword3
	Version           : :4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
