---
layout: page
title: "Q196835: HOWTO: Override the MFC Default Control Containment"
permalink: /kb/196/Q196835/
---

## Q196835: HOWTO: Override the MFC Default Control Containment

{% raw %}

	Article: Q196835
	Product(s): Microsoft C Compiler
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbole kbActiveX kbCOMt kbContainer kbMFC kbVC500 kbVC600 kbGrpDSMFCATL
	Last Modified: 06-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The MFC that ships with Microsoft Visual C++ 5.0 provides some very basic
	control container support. The majority of this containment support is
	implemented in undocumented or private classes. As an advanced procedure, it is
	possible to derive from these classes and override the default behavior of
	several of the MFC control container interface methods.
	
	WARNING: This functionality is based on private header files and classes of MFC
	and as such must be considered version specific. These files are subject to
	change and therefore, you use them at your own risk. If you use this article,
	Microsoft Technical Support will not be able to assist with any problems as this
	article uses undocumented classes.
	
	
	MORE INFORMATION
	================
	
	The MFC control container support involves three main classes: COccManager,
	COleControlContainer, and COleControlSite. COccManager is the master- controller
	for all control containers in one MFC process and is responsible for handing out
	pointers to COleControlSite and COleControlContainer objects. COccManager also
	has an IsDialogMessage method that implements message processing functionality
	needed by ActiveX control containers.
	
	COleControlContainer implements the container for one or more ActiveX controls.
	This container corresponds to one particular window in the container application
	that hosts several ActiveX controls and other standard controls. Typically, this
	is a dialog box. As the container object, COleControlContainer implements two
	interfaces: IOleInPlaceFrame and IOleContainer.
	
	For each control hosted in the control container object, there is a corresponding
	MFC control site object. This control site object is implemented by
	COleControlSite. As the one-on-one direct site object for a hosted ActiveX
	control, the COleControlSite implements several interfaces: IOleClientSite,
	IOleInPlaceSite, IOleControlSite, IPropertyNotifySink, IBoundObjectSite,
	INotifyDBEvents. COleControlSite also implements two IDispatch interfaces, one
	for ambient properties and the other as an event sink for the control.
	
	This article provides the steps required to override one of these three objects
	to change or add functionality at the interface level in COleControlContainer or
	COleControlSite.
	
	Steps to override COleControlContainer
	--------------------------------------
	
	1. Create a class derived from COleControlContainer. The constructor needs to
	  call the COleControlContainer constructor directly, as there is no default
	  COleControlContainer constructor:
	
	        CMyOleControlContainer::CMyOleControlContainer(CWnd* pWnd) :
	           COleControlContainer(pWnd)
	        {
	        }
	
	2. Create a class derived from COccManager. Add an empty constructor and an
	  empty virtual destructor.
	
	3. Override the COccManager::CreateContainer function to create and return a new
	  instance of your new COleControlContainer-derived class. You can do this by
	  adding the following method to your COccManager class definition:
	
	        virtual COleControlContainer* CreateContainer(CWnd* pWnd)
	        {
	           // Advanced control container applications may want to override.
	           return new CMyOleControlContainer(pWnd);
	        }
	
	4. Modify your call to AfxEnableControlContainer (probably in
	  CYourApp::InitInstance) to pass in an instance of your COccManager-derived
	  class:
	
	        CMyOccManager theManager;
	
	        // ...
	
	        BOOL CMfcaxscrvbApp::InitInstance()
	        {
	           // Initialize OLE libraries
	           if (!AfxOleInit())
	           // ...
	           AfxEnableControlContainer(&theManager);
	
	NOTE: For a CHtmlView derived class, its Create function calls
	AfxEnableControlContainer() causing it to override our initial custom
	COccManager class. To avoid this problem, you need to override
	CHtmlView::Create, copy all the code into your overridden Create function minus
	the call to AfxEnableC ntrolContainer(). Remember NOT to call the base class
	Create method since the original implementation did not.
	
	5. Include the Occimpl.h header file in your CMyOccManager implementation file
	  before the CMyOccManager header file. You may need to make a direct reference
	  in the #include statement because Occimpl.h is in the VC/MFC/SRC directory.
	
	6. Include the Occimpl.h header file in your CMyOleControlContainer
	  implementation file before the CMyOleControlContainer header file. Use the
	  AFX_DATA defines to insure that you import data from the classes defined in
	  Occimpl.h:
	
	        #undef AFX_DATA
	        #define AFX_DATA AFX_DATA_IMPORT
	        #include "c:\program files\devstudio\vc\mfc\src\occimpl.h"
	        #undef AFX_DATA
	        #define AFX_DATA AFX_DATA_EXPORT
	
	7. Follow the standard procedure to override an interface in the
	  CMyOleControlContainer class. For more information on how to do this, please
	  see the following article in the Microsoft Knowledge Base:
	
	  Q141277 HOWTO: Override an Interface in an MFC Application
	
	Here is a typical example that overrides the IOleInPlaceFrame interface:
	
	        // Inside header definition in .h.
	        class CMyOleControlContainer : public COleControlContainer
	        {
	        // ...
	           // Interface maps.
	           BEGIN_INTERFACE_PART(MyOleIPFrame, IOleInPlaceFrame)
	              INIT_INTERFACE_PART(CMyOleControlContainer, MyOleIPFrame)
	              STDMETHOD(GetWindow)(HWND*);
	              STDMETHOD(ContextSensitiveHelp)(BOOL);
	              STDMETHOD(GetBorder)(LPRECT);
	              STDMETHOD(RequestBorderSpace)(LPCBORDERWIDTHS);
	              STDMETHOD(SetBorderSpace)(LPCBORDERWIDTHS);
	              STDMETHOD(SetActiveObject)(LPOLEINPLACEACTIVEOBJECT,
	                                         LPCOLESTR);
	              STDMETHOD(InsertMenus)(HMENU, LPOLEMENUGROUPWIDTHS);
	              STDMETHOD(SetMenu)(HMENU, HOLEMENU, HWND);
	              STDMETHOD(RemoveMenus)(HMENU);
	              STDMETHOD(SetStatusText)(LPCOLESTR);
	              STDMETHOD(EnableModeless)(BOOL);
	              STDMETHOD(TranslateAccelerator)(LPMSG, WORD);
	           END_INTERFACE_PART(MyOleIPFrame)
	
	           DECLARE_INTERFACE_MAP()
	        };
	
	        // Inside implementation file .cpp:
	
	        BEGIN_INTERFACE_MAP(CMyOleControlContainer, COleControlContainer)
	           INTERFACE_PART(CMyOleControlContainer, IID_IOleInPlaceFrame,
	                          MyOleIPFrame)
	        END_INTERFACE_MAP()
	
	        STDMETHODIMP CMyOleControlContainer::XMyOleIPFrame::QueryInterface(
	           REFIID iid, LPVOID* ppvObj)
	        {
	           METHOD_PROLOGUE_EX_(CMyOleControlContainer, MyOleIPFrame)
	           return (HRESULT)pThis->InternalQueryInterface(&iid, ppvObj);
	        }
	
	        STDMETHODIMP_(ULONG) CMyOleControlContainer::XMyOleIPFrame::AddRef()
	        {
	           METHOD_PROLOGUE_EX_(CMyOleControlContainer, MyOleIPFrame)
	           return (ULONG)pThis->InternalAddRef();
	        }
	
	        // ...
	        // Cut and paste all of this code from the MFC source in Occimpl.h
	        // and change all references to COleControlContainer to reference
	        // your class. Then, modify methods as desired. For example, here is
	        // a customized enablemodeless call:
	
	        STDMETHODIMP
	           CMyOleControlContainer::XMyOleIPFrame::EnableModeless(BOOL f)
	        {
	           METHOD_PROLOGUE_EX(CMyOleControlContainer, MyOleIPFrame)
	
	           CWinApp* pApp = AfxGetApp();
	           if (!pApp)
	              return E_FAIL;
	
	           pApp->EnableModeless(f);
	           return S_OK;
	        }
	
	Steps to override COleControlSite
	---------------------------------
	
	To override COleControlSite, follow the same steps as for COleControlContainer,
	substituting COleControlSite for COleControlContainer where appropriate. Some
	relevant code snippets follow:
	
	     CMyOleControlSite::CMyOleControlSite(COleControlContainer* pCtrlCont) :
	        COleControlSite(pCtrlCont)
	     {
	
	     }
	
	The COccManager::CreateSite is used to create COleControlSite objects. To use
	your ControlSite class, add the following method to your COccManager class
	definition:
	
	     virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont)
	     {
	        // advanced control container override
	        return new CMyOleControlSite(pCtrlCont);
	     }
	
	A typical example that overrides the IOleControlSite interface follows:
	
	     // Inside header definition in .h:
	     class CMyOleControlSite : public COleControlSite
	     {
	     // ...
	        // Interface maps.
	        BEGIN_INTERFACE_PART(MyOleControlSite, IOleControlSite)
	           INIT_INTERFACE_PART(CMyOleControlSite, MyOleControlSite)
	           STDMETHOD(OnControlInfoChanged)();
	           STDMETHOD(LockInPlaceActive)(BOOL fLock);
	           STDMETHOD(GetExtendedControl)(LPDISPATCH* ppDisp);
	           STDMETHOD(TransformCoords)(POINTL* lpptlHimetric,
	              POINTF* lpptfContainer, DWORD flags);
	           STDMETHOD(TranslateAccelerator)(LPMSG lpMsg, DWORD grfModifiers);
	           STDMETHOD(OnFocus)(BOOL fGotFocus);
	           STDMETHOD(ShowPropertyFrame)();
	        END_INTERFACE_PART(MyOleControlSite)
	
	        DECLARE_INTERFACE_MAP()
	     };
	
	     // Inside implementation file .cpp:
	
	        BEGIN_INTERFACE_MAP(CMyOleControlSite, CMyOleControlSite)
	           INTERFACE_PART(CMyOleControlSite, IID_IOleControlSite,
	                          MyOleControlSite)
	        END_INTERFACE_MAP()
	
	     STDMETHODIMP_(ULONG) CMyOleControlSite::XMyOleControlSite::AddRef()
	     {
	        METHOD_PROLOGUE_EX_(CMyOleControlSite, OleControlSite)
	        return (ULONG)pThis->InternalAddRef();
	     }
	
	     STDMETHODIMP_(ULONG) CMyOleControlSite::XMyOleControlSite::Release()
	     {
	        METHOD_PROLOGUE_EX_(CMyOleControlSite, OleControlSite)
	        return (ULONG)pThis->InternalRelease();
	     }
	
	     // ...
	     // Cut and paste all of this code from the MFC source in Occimpl.h
	     // and change all references to COleControlSite to reference your
	     // class. Then, modify methods as desired.
	
	REFERENCES
	==========
	
	  Q141277 HOWTO: Override an Interface in an MFC Application
	
	  (c) Microsoft Corporation 1999, All Rights Reserved.
	  Contributions by Jason Strayer, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbole kbActiveX kbCOMt kbContainer kbMFC kbVC500 kbVC600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : :5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
