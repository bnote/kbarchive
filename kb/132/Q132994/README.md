---
layout: page
title: "Q132994: Games (A-H) Requiring or Performing Better in MS-DOS Mode"
permalink: /kb/132/Q132994/
---

## Q132994: Games (A-H) Requiring or Performing Better in MS-DOS Mode

{% raw %}

	Article: Q132994
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): kb3rdparty kbenv win95 appscomp kbAppCompatibility
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article lists games (A-H) that must be run in MS-DOS mode. Additional
	information is provided when available.
	
	For information about running games in MS-DOS mode, please see the "Running an
	Application in MS-DOS Mode" section later in this article.
	
	MORE INFORMATION
	================
	
	1942: The Pacific Air War by Microprose
	---------------------------------------
	
	Executables: 1942.BAT, 1942.EXE
	
	1942: The Pacific Air War requires MS-DOS mode.
	
	Aces of the Deep by Dynamix (Sierra Online)
	-------------------------------------------
	
	Executables: AOD.BAT, AOD.EXE
	
	If you run Aces of the Deep in Windows 95, it encounters internal assertion
	failures. Run it in MS-DOS mode to resolve these errors.
	
	
	Aegis: Guardian of the Fleet
	----------------------------
	
	Executables: AEGIS.EXE, AEGISV.EXE
	
	Aegis sets the timer rate to a speed faster than the game can handle. Running it
	in MS-DOS mode may alleviate some of the problem.
	
	Archon Ultra by Free Fall Associates
	------------------------------------
	
	Executable: ARCHON.EXE
	
	Archon Ultra sets the timer rate to a speed too fast for Windows 95 to handle
	comfortably. Running it in MS-DOS mode allows the program to run at full speed.
	
	Arctic Baron by Ready Soft
	--------------------------
	
	Executable: START.EXE
	
	Arctic Baron requires MS-DOS mode to run in Windows 95.
	
	Are You Afraid of the Dark? by Viacom
	-------------------------------------
	
	Executable: AFRAID.BAT
	
	Are You Afraid of the Dark? uses virtual memory in a way that causes erratic
	sound and speech. Depending on your system configuration, it may also fail
	during sound and video playback. Run it in MS-DOS mode to resolve these
	problems.
	
	
	Battle Chess 4000 by Interplay
	------------------------------
	
	Battle Chess requires MS-DOS mode.
	
	Battledrome by Dynamix (Sierra Online)
	--------------------------------------
	
	Executable: BD.EXE
	
	Battledrome is not compatible with VSHARE; therefore, it must be run in MS-DOS
	mode.
	
	
	Beneath a Steel Sky
	-------------------
	
	Executable: SKY.EXE
	
	Beneath a Steel Sky uses a memory model not compatible with Windows 95. Run it in
	MS-DOS mode.
	
	
	Bioforge by Origin
	------------------
	
	Executable: BIOFORGE.EXE
	
	Bioforge makes incorrect assumptions about the system memory configuration when
	Windows 95 is running. This causes it to fail to detect most of the memory
	installed in the computer. It must be run in MS-DOS mode.
	
	
	Bloodnet by Microprose
	----------------------
	
	Bloodnet works only when the DMA channel is set to 7 if you are using the Pro
	Audio Spectrum sound card. The game tries to reconfigure the sound device to DMA
	7 automatically. This is not tolerated by the virtual device driver (VxD).
	
	To resolve this issue, you can use one of the following methods:
	
	- Use Sound Blaster-compatible mode on your PAS.
	
	- Reconfigure the PAS device to DMA 7.
	
	- Use MS-DOS mode.
	
	Brett Hull Hockey 95 by Accolade
	--------------------------------
	
	Executable: HOCKEY.EXE
	
	Brett Hull Hockey 95 requires MS-DOS mode and a properly set BLASTER environment
	variable in order to play sound.
	
	Bridge Olympiad by Quantum Quality Products
	-------------------------------------------
	
	Executable: BO.BAT
	
	Bridge Olympiad directly accesses the hard disk ports resulting in a conflict
	with Windows 95 disk drivers. It must be run in MS-DOS mode.
	
	Chessmaster 3000 by The Software Toolworks
	------------------------------------------
	
	Chessmaster 3000 requires MS-DOS mode. Even in MS-DOS mode, if digital sound is
	enabled, your computer may (stop responding) hang after sound effects.
	
	Chuck Yeager's Advanced Flight Simulator,
	Chuck Yeager's Air Combat by Electronic Arts
	--------------------------------------------------------------------------------------
	
	Executables: AFS.EXE, AFS.BAT
	
	In order to play speech and sound effects through the computer's built-in
	speaker, these programs set the timer rate to a speed too fast for Windows 95 to
	handle comfortably. Running the programs in MS-DOS mode allows them to run at
	full speed.
	
	Chuck Yeager's Advanced Flight Simulator may also encounter copy protection
	problems if not run in MS-DOS mode.
	
	
	Club Dead by Viacom
	-------------------
	
	Executable: DEAD.EXE
	
	Club Dead contains timing-related problems that cause the program to fail. It
	must be run in MS-DOS mode.
	
	
	Comanche Overkill by Nova Logic
	-------------------------------
	
	Executables: C.BAT, COMANCHE.EXE
	
	Comanche Overkill requires complete control of the computer and must be run in
	MS-DOS mode. Windows 95 should automatically run this program in MS-DOS mode. If
	it does not, remove all .PIF files associated with COMANCHE.EXE or C.BAT and
	restart the game.
	
	
	Command Adventures Starship by Future Visionary, Inc. and Merit Software
	------------------------------------------------------------------------
	
	Executable: STARSHIP.COM
	
	Command Adventures Starship does not check whether memory allocations were
	successful and corrupts itself if a memory allocation subsequently fails. You
	may be able to run this game in Windows 95 by adding "/NUMHANDLES=40" (without
	the quotation marks) to the HIMEM.SYS line in the CONFIG.SYS file. This setting
	increases the number of XMS handles available. If this does not work, run
	Command Adventures Starship in MS-DOS mode.
	
	
	Curse of the Catacombs by FroggMan
	----------------------------------
	
	Curse of the Catacombs requires MS-DOS mode.
	
	Cyber Race
	----------
	
	Executable: CR.BAT
	
	Cyber Race refuses to run in any protected-mode operating system. It must be run
	in MS-DOS mode.
	
	
	CyberWar by Sales Curve International
	-------------------------------------
	
	If you use an ESS ES688 and no MIDI, you must use IRQ 5. If you have problems,
	run CyberWar in MS-DOS mode.
	
	Cyclones by Strategic Simulations (SSI)
	---------------------------------------
	
	Executable: CYCLONES.EXE
	
	Cyclones makes incorrect assumptions about the system memory configuration when
	Windows 95 is running.
	
	NOTE: Cyclones may fail to run even in MS-DOS mode if the computer has 64
	megabytes (MB) of memory or more. Contact the manufacturer if you are
	encountering this problem.
	
	
	Dark Forces by Lucas Arts
	-------------------------
	
	During the installation of Dark Forces, the sound detection must run twice to
	detect AWE 32. Furthermore, Dark Forces may fail to run in Windows 95 on some
	computers. If you encounter problems, run Dark Forces in MS-DOS mode.
	
	Darkseed by Cyberdreams, Inc.
	-----------------------------
	
	Executable: DS.BAT
	
	Darkseed has a timing-related problem in its sound code that causes it to hang.
	The problem may be resolved when it is run in MS-DOS mode.
	
	
	Death Gate by Legend Entertainment Company
	------------------------------------------
	
	Death Gate fails on some sound cards (such as ESS ES688 and Aztech WA cards). Run
	Death Gate in MS-DOS mode if you encounter problems.
	
	Dino Park Tycoon 1.0 by MECC
	----------------------------
	
	Dino Park Tycoon runs in Windows 95 only if sound is disabled. To use sound, you
	must run this game in MS-DOS mode.
	
	Dognapped by FroggMan
	---------------------
	
	Dognapped sets the timer rate too fast for some computers. If you encounter
	problems with Dognapped in Windows 95, run it in MS-DOS mode.
	
	Dracula Unleashed by Viacom
	---------------------------
	
	Executable: DRACULA.EXE
	
	Dracula manipulates the interrupt flag register in a manner incompatible with
	Windows 95. It must be run in MS-DOS mode.
	
	
	Dragon's Lair by Merit Software
	-------------------------------
	
	Executables: DL.EXE, DRAGON.EXE
	
	Although Dragon's Lair runs in Windows 95, the sound is erratic. It runs better
	in MS-DOS mode.
	
	DreamForge
	----------
	
	DreamForge requires MS-DOS mode.
	
	Dungeon Master by Software Heaven
	---------------------------------
	
	Dungeon Master requires MS-DOS mode.
	
	Eight Ball Deluxe by Amtex
	--------------------------
	
	Eight Ball Deluxe requires MS-DOS mode.
	
	Empire Deluxe
	-------------
	
	Empire Deluxe sets the timer rate to a speed too fast for Windows 95 to handle
	comfortably. It runs, although slowly. Running Empire Deluxe in MS-DOS mode
	allows it to run at full speed.
	
	Falcon AT by Spectrum Holobyte
	------------------------------
	
	Falcon AT requires MS-DOS mode.
	
	
	Fields of Glory by Spectrum Holobyte
	------------------------------------
	
	Fields of Glory requires MS-DOS mode.
	
	FIFA International Soccer by Electronic Arts
	--------------------------------------------
	
	Executable: FIFA.EXE
	
	FIFA International Soccer uses a memory model that is not compatible with Windows
	95. It must be run in MS-DOS mode.
	
	
	Fifth Fleet
	-----------
	
	Executable: FLEET.EXE
	
	Fifth Fleet has a timing-related problem in its sound code that causes it not to
	recognize the sound card. The problem may be resolved when Fifth Fleet is run in
	MS-DOS mode.
	
	
	Flight of the Intruder by Spectrum Holobyte
	-------------------------------------------
	
	Flight of the Intruder requires MS-DOS mode.
	
	Flight Simulator Tool Kit - World War II by Spectrum Holobyte
	-------------------------------------------------------------
	
	Executable: WWII.BAT
	
	Flight Simulator Tool Kit requires MS-DOS mode to play sounds properly.
	
	
	Freakin' Funky Fuzzballs by Sir-Tech
	------------------------------------
	
	Freakin' Funky Fuzzballs requires MS-DOS mode.
	
	Front Page Sports by Dynamix (Sierra Online)
	--------------------------------------------
	
	Executable for Front Page Sports Football Pro!: HIKE.COM
	Executable for Front Page Sports Football Pro '95: HIKE.COM
	Executable for Front Page Sports Baseball '94: PLAYBALL.COM
	
	If sound effects are enabled, the Front Page Sports programs use Virtual Direct
	Memory Access Services (VDS) incorrectly and must be run in MS-DOS mode.
	
	
	FX Fighter by Argonaut Software
	-------------------------------
	
	FX Fighter encounters memory problems (such as page faults) when run in Windows
	95. It must be run in MS-DOS mode.
	
	
	Gabriel Knight for MS-DOS by Sierra Online
	------------------------------------------
	
	Executable: GKCD.BAT
	
	Gabriel Knight requires MS-DOS mode.
	
	Game Pak III by The Software Toolworks
	--------------------------------------
	
	Game Pak III requires MS-DOS mode.
	
	Goblins,
	
	Goblins 2 by Sierra Online
	-----------------------------------
	
	Executables: GO.BAT, GOB.BAT
	
	These programs set the timer rate to a speed too fast for Windows 95 to handle
	comfortably and must be run in MS-DOS mode.
	
	Grand Prix by Road and Track
	----------------------------
	
	Grand Prix does not run well in an MS-DOS session when you are using the PC
	speaker as the designated sound output device. System performance slows
	considerably because of the increased timer load by the PC speaker. To boost
	performance with this game, run the game in MS-DOS mode, or turn off the PC
	speaker sound.
	
	Great Naval Battles 1939-1942 by Strategic Simulations (SSI)
	------------------------------------------------------------
	
	This version of Great Naval Battles requires MS-DOS mode, and you must use
	VINSTALL to detect the correct VESA driver. Great Naval Battles Vol. II
	1942-1943 - Guadalcanal should run in Windows 95.
	
	Harpoon 2 by 360 Pacific
	------------------------
	
	Executable: HARPOON2.EXE
	
	The MS-DOS extender used by Harpoon is not compatible with Windows 95. It must be
	run in MS-DOS mode.
	
	
	Helicopter Simulator by Sierra Online
	-------------------------------------
	
	Executable: HELO.COM
	
	Helicopter Simulator must run in MS-DOS mode due to the way it implements
	copy-protection.
	
	Hell - A Cyberpunk Thriller
	---------------------------
	
	Executables: HELL.*, HECK.*
	
	Hell - A Cyberpunk Thriller requires MS-DOS mode to play sounds properly.
	
	
	The Horde by Crystal Dynamics
	-----------------------------
	
	Executable: HORDE.EXE
	
	The Horde manipulates the interrupt flag register in a manner incompatible with
	Windows 95. It must be run in MS-DOS mode.
	
	
	The Humans by GameTek
	---------------------
	
	Executable: HUMANS.EXE
	
	The Humans sets the timer rate to a speed too fast for Windows 95 to handle
	comfortably. It runs, although slowly. Running The Humans in MS-DOS mode allows
	it to run at full speed.
	
	Running an Application in MS-DOS Mode
	-------------------------------------
	
	Windows 95 usually runs programs that require MS-DOS mode in MS-DOS mode
	automatically. If it does not, delete the corresponding .PIF file and
	double-click the program icon again. Note that .PIF files usually have the same
	name as the program file, but with a .PIF extension instead of the .BAT, .COM,
	or .EXE extension. The corresponding .PIF file can be found in one of the
	following locations:
	
	- In the folder that contains the program file.
	
	- In the hidden PIF folder in the Windows 95 folder.
	
	- In a folder specified by your PATH statement.
	
	To make certain you find all copies of the .PIF file, use the Find Files Or
	Folders feature.
	
	If Windows 95 does not configure the program to run in MS-DOS mode automatically,
	follow these steps:
	
	1. Click the executable file with the right mouse button, then click Properties
	  on the menu that appears.
	
	2. On the Program tab, click the Advanced button.
	
	3. Click the MS-DOS Mode check box to select it.
	
	4. You can usually use the Use Current MS-DOS Configuration option. However,
	  some programs may require that you use the Specify A New Configuration
	  option. Consult the program's documentation for sample CONFIG.SYS and
	  AUTOEXEC.BAT files.
	
	5. Click OK.
	
	These steps cause the program to run in MS-DOS mode. You may need to optimize the
	settings if the program requires a mouse, expanded memory, a CD-ROM drive, or a
	sound card. Consult the program's documentation to determine if it has specific
	needs.
	
	NOTE: You may have to double-click the program icon in Windows Explorer or My
	Computer, or type the program name in the Run dialog box, for the program's
	settings to take effect. Typing the program name at an MS-DOS prompt does not
	always cause the program's settings to be used.
	
	Additional query words: single sdam fs5
	
	======================================================================
	Keywords          : kb3rdparty kbenv win95 appscomp kbAppCompatibility 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
