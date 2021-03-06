---
layout: page
title: "Q308523: Program Stops Responding and Black Screen Appears with IBM Mouse"
permalink: /kb/308/Q308523/
---

## Q308523: Program Stops Responding and Black Screen Appears with IBM Mouse

{% raw %}

	Article: Q308523
	Product(s): Microsoft Home Games
	Version(s): 
	Operating System(s): 
	Keyword(s): kbimu
	Last Modified: 28-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MechWarrior 4: Vengeance 
	- Microsoft Links LS 2000 
	- Microsoft Links 2001 
	- Microsoft Crimson Skies 
	- Microsoft Age of Empires II Expansion: The Conquerors 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start Microsoft MechWarrior or Microsoft Links, the computer
	may stop responding (hang) with a black screen and a blue title bar.
	
	CAUSE
	=====
	
	This issue occurs when the International Business Machines (IBM) Mouse Suite or
	IBM Scoll Point 3 utility software are installed. Some versions of this software
	are incompatible with the products listed at the beginning of this article.
	
	RESOLUTION
	==========
	
	To resolve this issue, you must remove the IBM Mouse Suite or IBM Scoll Point 3
	utility software. Removal instructions should be included with your mouse
	documentation.
	For information about how to contact , click the appropriate article number in
	the following list to view the article in the Microsoft Knowledge Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	  Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	
	
	Add MechWarrior Vengeance Parameter
	-----------------------------------
	
	To manually add parameters to the command line in the MechWarrior Vengeance
	shortcut:
	
	1. Right-click MechWarrior Vengeance shortcut icon on your Desktop and then
	  click Properties.
	
	2. Click the Shortcut tab.
	
	3. In the Target box, press END, press the SPACEBAR, and then type the
	  "-noautoconfig" parameter.
	
	  As an example, the following sample command line includes parameter:
	
	  C:\Program Files\Microsoft Games\MechWarrior Vengeance\Mw4.exe -noautoconfig
	
	  NOTE: Parameters are not case-sensitive.
	
	4. Click Apply or OK.
	
	5. Start the game.
	
	
	MORE INFORMATION
	================
	
	The third-party products that are discussed in this article are manufactured by
	companies that are independent of Microsoft. Microsoft makes no warranty,
	implied or otherwise, regarding the performance or reliability of these
	products.
	
	Microsoft provides third-party contact information to help you find technical
	support. This contact information may change without notice. Microsoft does not
	guarantee the accuracy of this third-party contact information.
	
	Additional query words: msgame mech4 links2000 links2001 crimson skies empires
	
	======================================================================
	Keywords          : kbimu 
	Technology        : kbHomeProdSearch kbLinkGolfSearch kbGamesSearch kbGolfSearch kbCrimsonSkiesSearch kbAOESearch kbAOE2ExpConquerors kbCrimsonSkies kbLinks2001 kbLinksLS2000
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
