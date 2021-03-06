---
layout: page
title: "Q175491: ODE97: Step-by-Step Example of Creating/Compiling a Help File"
permalink: /kb/175/Q175491/
---

## Q175491: ODE97: Step-by-Step Example of Creating/Compiling a Help File

{% raw %}

	Article: Q175491
	Product(s): Microsoft Access Distribution Kit
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 16-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	Advanced: Requires expert coding, interoperability, and multiuser skills.
	
	SUMMARY
	=======
	
	This article demonstrates how to create a practice topic file using Microsoft
	Word 97, and then shows you how to compile it in Microsoft Help Workshop.
	
	MORE INFORMATION
	================
	
	The general steps in creating and compiling a topic file are as follows. Each
	step is fully described later in this article.
	
	1. Create your topic information.
	
	2. Format your text.
	
	3. Separate your topics.
	
	4. Identify your topics so that WinHelp can find them.
	
	5. Connect your topics.
	
	6. Add graphics.
	
	7. Save your topic file.
	
	8. Compile your topic file in Help Workshop.
	
	Create Your Topic Information
	-----------------------------
	
	To create your topic information, open Microsoft Word and type the following
	information into a new document:
	
	  This is the first topic in my sample topic file. What I type here
	  will appear in my sample Help file. I can format the text in my
	  topic file in different ways, including italic and bold. I can
	  also change the size and color of my text.
	
	  I can provide more information about a word by turning it into a
	  pop-up. I can also turn a word into a jump. A jump displays
	  another topic when a user clicks it.
	
	  I can add graphics, sounds, and video clips to my sample Help
	  file. The following is a graphic that I have added to my Help
	  file.
	
	  This is a pop-up. A pop-up is a window that appears on top of a
	  window or dialog box.
	
	  This is a jump. When a user clicks a jump, the Help topic that I
	  specify is displayed.
	
	Format Your Text
	----------------
	
	So that you can see how your topic file is affected by text formatting, make the
	following changes to your sample text:
	
	- Format the word "italic" using the font style Italic.
	
	- Format the word "bold" using the font style Bold.
	
	- Format the word "size" using the font size 8.
	
	- Format the word "color" using the font color Red.
	
	Separate Your Topics
	--------------------
	
	You separate your topics by inserting a manual page break. To separate your
	topics, follow these steps:
	
	1. Place the insertion point before the words "This is a pop-up," and then
	  insert two manual page breaks.
	
	2. Place the insertion point before the words "This is a jump," and then insert
	  a manual page break.
	
	Identify Your Topics So That WinHelp Can Find Them
	--------------------------------------------------
	
	You identify each topic by assigning a topic ID, which makes it possible for
	WinHelp to find them. You assign a topic ID by inserting a footnote in the
	topic. To assign IDs to your topics, follow these steps:
	
	1. Place the insertion point before the words "This is the first."
	
	2. On the Insert menu, click Footnote.
	
	3. In the Footnote And Endnote box, under Insert, click Footnote, and under
	  Numbering, click Custom Mark.
	
	4. In the Custom Mark text box, type "#" (without the quotation marks), and then
	  click OK.
	
	5. In the bottom pane of the Footnote window, type "MyTopic" (without the
	  quotation marks) to the right of the number sign (#). Click Close.
	
	6. Place the insertion point before the first words "This is a pop-up."
	
	7. Follow steps 2 through 4 again. In the bottom pane of the Footnote window,
	  type "MyPopup" (without the quotation marks). Click Close.
	
	8. Place the insertion point before the words "This is a jump."
	
	9. Follow steps 2 through 4 once more. In the bottom pane of the Footnote
	  window, type MyJump. Click Close.
	
	Connect Your Topics
	-------------------
	
	Now that the topic IDs have been assigned, you can create references to the
	topics anywhere in your Help files.
	
	NOTE: In the following steps you will be working with hidden text, so be sure
	Word is set to display hidden text. For information about displaying hidden text
	in Word, search the Help Index for "hidden text, reviewing."
	
	To connect your pop-up, follow these steps:
	
	1. In the second paragraph of your first topic, place the insertion point
	  directly after the period that follows the words "into a pop-up."
	
	2. Type the topic ID that you assigned to the pop-up text. This should be
	  MyPopup.
	
	3. Select the characters "pop-up." and then apply the single-underline Font
	  character style.
	
	4. Select the words "MyPopup", and then apply the Hidden font character style.
	
	5. In the second sentence of the second paragraph of your first topic, place the
	  insertion point directly after the period that follows the word "jump."
	
	6. Type the topic ID that you assigned to the jump text. This should be MyJump.
	
	7. Select the following characters "jump." and then apply the double- underline
	  font style.
	
	8. Select the topic ID, MyJump, and then apply the hidden character style.
	
	  For examples of how jumps and pop-ups should look in your topic file, search
	  the Microsoft Help Workshop Help Index for "pop-up windows," and then "To
	  create a jump to a topic or pop-up topic."
	
	Add Graphics
	------------
	
	Add an illustrative graphic to your Help topic. You can use any bitmap file that
	you have on your hard disk. There are sample BMP files in the Windows folder.
	
	1. Place the insertion point on the first blank line before the sentence "This
	  is a popup."
	
	2. On the Insert menu, point to Picture, and then click From File.
	
	3. In the Insert Picture box, in the Files Of Type list box, select Windows
	  Bitmap (*.bmp;*.dib;*.rle). Select any BMP file in the Name box, and then
	  click Insert.
	
	  NOTE: If you are using the Help Workshop application that is included in the
	  Microsoft Office 97 Developer Edition Tools (ODE), and you are adding bitmaps
	  to your topic file, you will need to download the new help compiler from the
	  Microsoft Web site before you can compile the file.
	
	  For more information about obtaining this file, please see the following
	  article in the Microsoft Knowledge Base:
	
	  Q164012 WD97 Error Compiling Word 97 RTF in Help Compiler, Help WorkShop
	
	
	Save Your Topic File
	--------------------
	
	1. On the File menu, click Save As. In the Save As dialog box, in the Save As
	  Type box, select Rich Text Format (*.rtf).
	
	2. In the File Name box, type "Myhelp" (without the quotation marks), and then
	  click Save.
	
	  NOTE: Be sure to save the file in the Help Workshop folder.
	
	Compile Your Topic File in Help Workshop
	----------------------------------------
	
	1. In Help Workshop, on the File menu, click New.
	
	2. In the New box, select Help Project, and then click OK.
	
	3. In the File Name box, type a name for the project(.hpj) file, and then click
	  Save.
	
	4. On the Help Project screen, click Files.
	
	5. In the Topic Files box, click Add, select your topic file from the
	  appropriate folder, and then click Open.
	
	6. Once your topic file is added to the Topic Files list, click OK. You should
	  now have two sections in your project file: one section for Options; one
	  section for Files.
	
	7. To add bitmap files to your project file, click Bitmaps, and then click the
	  Add button in the Bitmap Folders dialog box.
	
	8. Select the path to your bitmap files, and then click OK. Click OK again in
	  the Bitmap Folders box.
	
	9. Click Save And Compile. Help Workshop should compile and save your project
	  file.
	
	10. On the File menu, click Run Winhelp. In the View Help File dialog box, click
	  View Help.
	
	11. In the Find Setup Wizard dialog box, click Next. Click Finish.
	
	12. Click OK to the message "Unable to display the Find tab. (177)."
	
	  NOTE: This message occurs because your keyword has no topic title to
	  display.
	
	  Your Help file should appear on the screen.
	
	For more information about compiling your Help file, search the Microsoft Help
	Workshop Help Topics for "compiling, specifying which topics to include."
	
	REFERENCES
	==========
	
	For more information about creating Help files, please see the following
	articles in the Microsoft Knowledge Base:
	
	  Q171958 ODE97: Tips for Creating and Compiling Your Windows Help File
	
	  Q163939 ODE97: Help Workshop Help Topics Contents
	
	Additional query words: inf
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbOfficeSearch kbAudDeveloper kbOffice97Search kbOffice97 kbOffice97DevSearch
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
