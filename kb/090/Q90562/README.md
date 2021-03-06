---
layout: page
title: "Q90562: Using OpenDriver() to Communicate Data to Installable Drv"
permalink: /kb/090/Q90562/
---

## Q90562: Using OpenDriver() to Communicate Data to Installable Drv

{% raw %}

	Article: Q90562
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 06-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The lParam parameter supplied to the OpenDriver() call can be used to
	communicate information from a Windows-based application or dynamic-link library
	(DLL) to an installable driver. Windows resolves the call to OpenDriver() to
	three subsequent calls to the DriverProc() of the installable device driver; the
	third call calls the driver's DriverProc() with the message set to DRV_OPEN and
	lParam2 set to the lParam supplied to OpenDriver(). Thus, the DriverProc() could
	use the lParam2 supplied to process instance-specific information.
	
	One problem with this approach is that the control panel can call OpenDriver()
	with lParam2 set to 0 (zero) if a control panel application is being provided
	for that driver; thus, the DriverProc() of the installable driver cannot expect
	this parameter to contain valid communication values at all times.
	
	MORE INFORMATION
	================
	
	To work around this problem, you should set aside a dedicated initialization
	message greater than DRV_USER and call SendDriverMessage() with that value as
	the message parameter after calling OpenDriver() to open the installable device
	driver.
	
	Note that because the hDriver parameter passed to DriverProc() is unique with
	every call to OpenDriver(), you can associate instanced data with each instance
	of the driver. Alternatively, the DRV_OPEN switch in your DriverProc() could
	check whether lParam2 is 0 (zero) and take action accordingly. This technique,
	however, bears the potential problem that any application or DLL that
	erroneously opens the driver with a nonzero lParam2 parameter can confuse the
	driver significantly.
	
	For multimedia drivers, MMSYSTEM.DLL takes a slightly different approach to work
	around this problem. Aside from DriverProc(), each multimedia driver must export
	a second message-processing function called xxxMessage (where xxx is either of
	wod, wid, mod, mid, or aux, respectively; depending on the type of driver).
	MMSYSTEM.DLL broadcasts initialization messages to these respective functions
	upon Windows boot time; the message parameters sent to the message functions are
	labeled WODM_INIT, WIDM_INIT, MODM_INIT, MIDM_INIT, and AUXM_INIT, respectively,
	and are provided for one-time initialization.
	
	The xxxMessage functions cannot fail the xxxM_INIT messages; however,
	MMSYSTEM.DLL will call the message processing functions with their respective
	GETNUMDEVS messages immediately after sending the xxxM_INIT messages; if it
	finds the return value of that call to be greater than or equal to 0x10000 (in
	other words, if the HIWORD of the return value is not equal to zero), it will
	abort loading the driver.
	
	Additional query words: 3.10
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
