---
layout: page
title: "Q312105: HOWTO: Save Outlook E-mail to a Folder Other Than Sent Items"
permalink: /kb/312/Q312105/
---

## Q312105: HOWTO: Save Outlook E-mail to a Folder Other Than Sent Items

{% raw %}

	Article: Q312105
	Product(s): Microsoft FoxPro
	Version(s): 7.0
	Operating System(s): 
	Keyword(s): kbCOMt kbOOP kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 kbHOWTOmaster
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 7.0 
	- Microsoft Outlook 2002 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article demonstrates how to automate Microsoft Outlook 2002 to
	programmatically send e-mail messages from Visual FoxPro (VFP) 7.0 and have
	those messages saved in a folder other than the Sent Items folder.
	
	MORE INFORMATION
	================
	
	VFP developers often write applications that perform bulk e-mail operations.
	After the messages are sent, it is sometimes desirable to save the messages to a
	folder other than the default Sent Items folder. In this way, the messages sent
	by the application are kept separate from other messages sent through the same
	client, making them easier to find later.
	
	Although it is possible to programmatically specify a folder in which to save
	your sent e-mail messages (by using the CdoPR_SENTMAIL_ENTRYID CDO constant),
	the setting is ignored because the CDO (1.x) library hard-codes the value placed
	in the PR_SENTMAIL_ENTRYID field to the Sent Items folder. For additional
	information, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q192083 PRB: Setting PR_SENTMAIL_ENTRYID in CDO (1.x) Is Not Retained
	
	You can work around this problem by using the COPYTO() method of your e-mail
	message object to relocate the message to a folder of your choice before it is
	sent.
	
	The sample code below makes a copy of the message before it is sent, as opposed
	to moving or copying the message after it is sent. We do this because Outlook
	messages are typically not sent instantly; they may sit in the Outlook Outbox
	for a short time. As a result, code running in a loop that relies on a message
	being located in the default Sent Items folder may fail.
	
	The only drawback to this approach is that you will have a copy of the message in
	your alternate Sent Items folder even if the message was not successfully sent.
	This is not a major drawback, however, because people most often wish to retain
	sent messages for reference, not as proof of delivery.
	
	NOTE: This code was written and tested with VFP 7.0. With slight modification, it
	will work with any version of VFP. It was tested with Outlook 2002 from
	Microsoft Office XP, but should also work with Office 2000.
	
	The VFP 7.0 code below will:
	
	1. Log on to MAPI.SESSION.
	
	2. Compose a new e-mail message.
	
	3. Scan your message store(s) for the ID of the folder that you specify as your
	  alternate Sent Items folder.
	
	4. Copy the in-progress message to your alternate Sent Items folder and then
	  send the message.
	
	To use this sample code, follow these steps:
	
	1. Open Outlook, create a new folder, and name it "My Sent Items". You can
	  create the folder as a subfolder in any message store that you like.
	
	2. Copy the code below to a new program in VFP 7.0.
	
	3. Save and then run the program.
	
	  *-----------------------------------
	  * AUTHOR:   Trevor Hancock
	  * CREATED:  12/05/01 11:58:05 AM
	  * ABSTRACT: This sample code sends an e-mail message to the address
	  *           you specify. It then saves this message to a folder other
	  *           than the default Sent Items Outlook folder.
	  *
	  *           To use this code, create a new folder in Outlook named
	  *           "My Sent Items". You can later rename this folder to anything
	  *           you like, provided that you change the 1st #DEFINE
	  *           below accordingly.
	  *-----------------------------------
	  #DEFINE New_Sent_Folder              "My Sent Items"
	  #DEFINE CdoDefaultFolderSentItems    3
	
	  *--    Define our variables.
	  LOCAL loSession AS "mapi.session", ;
	  	loMessage AS OBJECT, ;
	  	loRecip AS OBJECT, ;
	  	loSentItems AS OBJECT, ;
	  	loSentMsg AS OBJECT, ;
	  	lcToWho AS STRING, ;
	  	lcSampleAddress AS STRING, ;
	  	lcNewSentFolderID AS STRING, ;
	  	loMsgCopy AS OBJECT
	
	  PUBLIC gcFolderID
	  gcFolderID = ""
	
	  *--    Set up the e-mail message.
	  lcSampleAddress = "trevorh@MICROSOFT.COM"
	  lcToWho = INPUTBOX("What address do you want to send the sample to?", + ;
	  	"Sample Message", lcSampleAddress)
	
	  *--    Cancel if an e-mail address is not specified.
	  IF EMPTY(lcToWho)
	  	MESSAGEBOX("Sample Canceled", "", 0, 3000)
	  	RETURN .F.
	  ENDIF
	
	  *--    Logon to MAPI and make the message.
	  loSession = CREATEOBJECT("mapi.session")
	  loSession.Logon()
	  lcNewSentFolderID = FindNewFolder(loSession)
	  loMessage = loSession.Outbox.MESSAGES.ADD
	
	  WITH loMessage
	  	.Subject = "Test Message"
	  	.TEXT = "Test Body"
	  	loRecip = .Recipients.ADD
	  	loRecip.NAME = ALLTRIM(lcToWho)
	  	loRecip.Resolve
	  	.UPDATE()
	  *--	Copy the msg to our alternate Sent Items folder.
	  	loMsgCopy = .CopyTo(lcNewSentFolderID)
	  	loMsgCopy.UPDATE()
	  *--	Passing .F. here to the SEND() method prevents a copy
	  *--	of this message being saved to the default Sent Items folder.
	  	.SEND(.F.)
	  ENDWITH
	
	  *--    Clean up.
	  loSession.Logoff
	  RELEASE ALL
	  CLEAR ALL
	
	  *~~~~~~~~~~~~~~~~~~~~~~~~~
	  FUNCTION FindNewFolder(lpoSession AS OBJECT)
	  	LOCAL loInfoStores AS OBJECT, ;
	  		loRootFolder AS OBJECT, ;
	  		liStoreCnt AS INTEGER
	
	  *-- Get an obj reference to the message stores in Outlook.
	  	loInfoStores = lpoSession.InfoStores
	
	  *-- Walk through the message store(s) (except any
	  *-- Public Folders) looking for a folder with the same name
	  *-- as the "New_Sent_Folder" constant.
	  	FOR liStoreCnt = 1 TO loInfoStores.COUNT
	  		IF !("PUBLIC FOLDERS" $ UPPER(loInfoStores.ITEM(liStoreCnt).NAME))
	  			loRootFolder = loInfoStores.ITEM(liStoreCnt).RootFolder
	  			WalkSubFolders(loRootFolder)
	
	  			IF !EMPTY(gcFolderID)
	  				RETURN gcFolderID
	  			ENDIF
	  		ENDIF
	  	ENDFOR
	
	  *~~~~~~~~~~~~~~~~~~~~~~~~~
	  FUNCTION WalkSubFolders(lpoFolder AS OBJECT)
	  	IF !EMPTY(gcFolderID)
	  		RETURN
	  	ENDIF
	
	  	IF UPPER(lpoFolder.NAME) = UPPER(New_Sent_Folder)
	  		gcFolderID = loFolder.ID
	  		RETURN
	  	ENDIF
	
	  	LOCAL loFolder AS OBJECT
	  	FOR EACH loFolder IN lpoFolder.Folders
	  		IF loFolder.Folders.COUNT > 0
	  			WalkSubFolders(loFolder)
	  			IF !EMPTY(gcFolderID)
	  				EXIT
	  			ENDIF
	  		ELSE
	  			IF UPPER(loFolder.NAME) = UPPER(New_Sent_Folder)
	  				gcFolderID = loFolder.ID
	  				EXIT
	  			ENDIF
	  		ENDIF
	  	NEXT
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCOMt kbOOP kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 kbHOWTOmaster 
	Technology        : kbVFPsearch kbOutlookSearch kbAudDeveloper kbOutlook2002 kbOutlook2002Search kbZNotKeyword3 kbVFP700
	Version           : :7.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
