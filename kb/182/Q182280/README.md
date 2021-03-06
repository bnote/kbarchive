---
layout: page
title: "Q182280: XADM: Store Crashes After Upgrade to 5.0 SP2 on Windows NT 3.51"
permalink: /kb/182/Q182280/
---

## Q182280: XADM: Store Crashes After Upgrade to 5.0 SP2 on Windows NT 3.51

{% raw %}

	Article: Q182280
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange, version 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After you upgrade from Microsoft Exchange Server 5.0 Service Pack 1 (SP1) to
	Exchange Server SP2 on a Windows NT 3.51 computer, the Microsoft Exchange
	information store may crash when the Internet Mail Service receives a MIME
	message that does not contain an associated media type. The Dr. Watson log file
	(Drwtsn32.log) may contain the following:
	
	  State Dump for Thread Id 0x126
	
	  eax=0000006d ebx=00000000 ecx=00000057 edx=00000000 esi=00405b2d
	  edi=00405b2c
	  eip=77f94bf1 esp=0596f93c ebp=0596f940 iopl=0         nv up ei ng nz na
	  po nc
	  cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000
	  efl=00000286
	
	  function: _strcmpi
	       77f94be0 55               push    ebp
	       77f94be1 8bec             mov     ebp,esp
	       77f94be3 56               push    esi
	       77f94be4 8b750c           mov     esi,[ebp+0xc]
	  ss:0636e262=????????
	       77f94be7 8b5508           mov     edx,[ebp+0x8]
	  ss:0636e262=????????
	       77f94bea b0ff             mov     al,0xff
	       77f94bec 0ac0             or      al,al
	       77f94bee 742c             jz      _strcmpi+0x3c (77f94c1c)
	       77f94bf0 ac               lodsb
	  ds:00405b2d=75
	  FAULT ->77f94bf1 8a22             mov     ah,[edx]
	  ds:00000000=??
	       77f94bf3 42               inc     edx
	       77f94bf4 38c4             cmp     ah,al
	       77f94bf6 74f4             jz      _strcmpi+0xc (77f94bec)
	       77f94bf8 2c41             sub     al,0x41
	       77f94bfa 3c1a             cmp     al,0x1a
	       77f94bfc 1ac9             sbb     cl,cl
	       77f94bfe 80e120           and     cl,0x20
	       77f94c01 02c1             add     al,cl
	       77f94c03 0441             add     al,0x41
	       77f94c05 86e0             xchg    al,ah
	       77f94c07 2c41             sub     al,0x41
	
	  *----> Stack Back Trace <----*
	
	  FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name
	  0596f940 77f12f3f 00000000 00405b2c 00000400 06e1c044 ntdll!_strcmpi
	  0596f954 004d0227 00000000 00405b2c 00000400 06e1c044 kernel32!lstrcmpiA
	  (FPO: [2,0,2])
	  0596f974 00473d5a 00473d7b 06e14f84 00000400 06e1c094 store!<nosymbols>
	  00000000 00000000 00000000 00000000 00000000 00000000 store!<nosymbols>
	
	CAUSE
	=====
	
	This problem only occurs on a Windows NT Server 3.51 computer. The problem is
	not observed on a computer running Windows NT Server 4.0. The crash is caused by
	trying to compare a null media type with another string.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server 5.0
	Service Pack 2. A supported fix is now available, but has not been fully
	regression-tested and should be applied only to systems experiencing this
	specific problem. Unless you are severely impacted by this specific problem,
	Microsoft recommends that you wait for the next Service Pack that contains this
	fix. Contact Microsoft Technical Support for more information.
	
	This fix has been posted to the following Internet location:
	
	  ftp://ftp.microsoft.com/bussys/exchange/exchange-public/fixes/Eng/Exchg5.0/Post-SP2-STORE/
	
	
	MORE INFORMATION
	================
	
	This problem was fixed by making sure the media type is not null before the
	comparison.
	
	Additional query words: XFOR MIME IMC IMS
	======================================================================
	Keywords          :  
	Technology        : kbZNotKeyword6 kbExchangeSearch kbExchange500 kbExchangeClientSearch kbZNotKeyword2
	Version           : WinNT:5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
