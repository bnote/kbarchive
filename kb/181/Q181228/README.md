---
layout: page
title: "Q181228: Download of File from IIS 4.0 Fails on IE 4.01 Client"
permalink: /kb/181/Q181228/
---

## Q181228: Download of File from IIS 4.0 Fails on IE 4.01 Client

{% raw %}

	Article: Q181228
	Product(s): Internet Information Server
	Version(s): WINDOWS:4.01; winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 07-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	- Microsoft Internet Explorer version 4.01 for Windows NT 4.0 
	- Microsoft Internet Explorer version 4.01 for Windows 95 
	- Microsoft Internet Explorer version 4.01 for Windows 3.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you connect an Internet Explorer (IE) version 4.01 to a Microsoft Internet
	Information Server (IIS) 4.0, and the IE 4.01 client attempts to download a file
	from the IIS 4.0 system via a Web page, the download may fail with the following
	error message:
	
	  The downloaded file is not available. This could be due to your
	  Security or Language settings or because the server was unable to
	  retrieve the requested file.
	
	CAUSE
	=====
	
	This is specific to IIS 4.0 and IE 4.01. When the Internet Information Server
	4.0 computer responds to the IE 4.01 client, the IIS 4.0 system responds with a
	specific HTTP header response that causes the IE 4.01 client to fail when
	attempting a file download:
	
	1. HTTP/1.1 200
	
	2. Cache-control: private
	
	3. application/x-unknown
	
	IIS 4.0 supports HTTP/1.1 200 by default, so it always sends this information to
	the IE 4.01 client. Also, IIS 4.0 sets the Cache-control directive to private by
	default. If the requested URL has no associated MIME type, then all three
	conditions are met, and the IE 4.01 client fails with the error message above.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, upgrade to Internet Explorer 4.01 Service Pack 1 or
	later. For information about obtaining a later version of Internet Explorer,
	visit the following Microsoft Web site:
	
	  http://www.microsoft.com/ie
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Internet Explorer 4.01 build
	2106.
	
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Contact
	Microsoft Technical Support for more information.
	
	Additional query words: ierelease
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbIEsearch kbiis400 kbZNotKeyword2 kbIENT400Search kbIE95Search kbIE310Search kbZNotKeyword3 kbIE401Win310 kbIE401Win95 kbIE401WinNT400
	Version           : WINDOWS:4.01; winnt:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
