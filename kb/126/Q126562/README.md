---
layout: page
title: "Q126562: Question Marks Appear During a Chat Session"
permalink: /kb/126/Q126562/
---

## Q126562: Question Marks Appear During a Chat Session

{% raw %}

	Article: Q126562
	Product(s): The Microsoft Network
	Version(s): WINDOWS:1.0,1.05,1.2,1.3,2.0,2.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network versions 1.0, 1.05, 1.2, 1.3, 2.0, 2.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are participating in a chat session on MSN, The Microsoft Network, you
	may see repeated question marks on the screen when another chat member sends a
	message.
	
	CAUSE
	=====
	
	An MSN member who is using a language (such as Japanese Kanji) that uses a
	Double Byte Character Set (DBCS) may be sending a message to a chat session that
	is taking place in a Single Byte Character Set (SBCS) language (such as
	English).
	
	RESOLUTION
	==========
	
	If you are receiving messages filled with question marks from a chat member, use
	the ignore feature to ignore messages from this member. To ignore a chat member,
	follow these steps:
	
	1. In the Member List, click the name of the member.
	
	2. On the View menu, click Ignore Members.
	
	3. Click the Ignore Messages From Selected Members check box to select it.
	
	4. Click OK.
	
	MORE INFORMATION
	================
	
	ASCII characters are represented by the values 0 to 127; ANSI includes ASCII but
	adds characters 128 through 255. In all languages, the ASCII characters are
	exactly the same, but characters 128-255 are used for letters specific to a
	language, based on the Code Page associated with the language. This approach
	handles the character differences for most languages in the world.
	
	Some languages (specifically East Asian languages such as Japanese Kanji, several
	dialects of Chinese, and Korean) cannot be represented with only 256 characters.
	The written characters in these languages are entire words rather than
	individual letters, so there are typically over 6000 different characters.
	
	To handle these languages, Unicode was introduced. Unicode uses two bytes for
	each character instead of the standard one byte for each character. This is
	called the Double Byte Character Set (DBCS), as opposed to the Single Byte
	Character Set (SBCS). The only difference is that all SBCS bytes start with 0
	and the first byte of all DBCS words (two bytes) starts with 1.
	
	When an MSN member using DBCS sends a text string into an SBCS chat session, the
	system converts all the characters to question marks.
	
	Additional query words: msn
	
	======================================================================
	Keywords          :  
	Technology        : kbMSNSearch kbMSN200 kbMSN130 kbMSN105 kbMSN250 kbMSN120
	Version           : WINDOWS:1.0,1.05,1.2,1.3,2.0,2.5
	
	=============================================================================
	

{% endraw %}
