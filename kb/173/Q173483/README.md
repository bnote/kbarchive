---
layout: page
title: "Q173483: HOWTO: Create Custom AppWizards that Generate Non-MFC Projects"
permalink: /kb/173/Q173483/
---

## Q173483: HOWTO: Create Custom AppWizards that Generate Non-MFC Projects

{% raw %}

	Article: Q173483
	Product(s): Microsoft C Compiler
	Version(s): WINNT:5.0
	Operating System(s): 
	Keyword(s): kbcode kbwizard kbVC500
	Last Modified: 17-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The AppWizard, included with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Visual C++ 5.0 custom AppWizards always generates an MFC-based project
	initially. Now the custom AppWizards can change the essential MFC project
	settings for the generated project through the new automation object model of
	Developer Studio.
	
	MORE INFORMATION
	================
	
	When a custom AppWizard generates a project, it cannot simply replace the
	automatically created .dsp project settings file. The project settings in the
	.dsp file are set by internal rules that assume all generated projects are MFC
	projects. However, Visual C++ 5.0's new object model allows custom AppWizards to
	modify tool settings such that all dependencies on MFC are removed from the
	resulting project.
	
	The CCustomAppWiz class in Visual C++ 5.0 now has a virtual override called
	CustomizeProject. CustomizeProject provides the custom wizard with an
	IBuildProject interface. The Configurations method of IBuildProject provides an
	IConfiguration interface for each build configuration in the project.
	IConfiguration can add and remove settings supplied to tools such as the
	compiler. Using these methods, a custom wizard can remove settings that add
	dependencies on MFC.
	
	Sample Code
	-----------
	
	Following is an example CustomizeProject override that demonstrates the removal
	of MFC dependencies:
	
	     #import "c:\Program Files\DevStudio\SharedIDE\bin\ide\devbld.pkg"
	
	     void CNoMfcCustWizAppWiz::CustomizeProject(IBuildProject* pProject)
	     {
	     using namespace DSProjectSystem;
	
	        long lNumConfigs;
	        IConfigurationsPtr pConfigs;
	        IBuildProjectPtr pProj;
	        // Needed to convert IBuildProject to the DSProjectSystem namespace
	        pProj.Attach((DSProjectSystem::IBuildProject*)pProject, true);
	
	        pProj->get_Configurations(&pConfigs);
	        pConfigs->get_Count(&lNumConfigs);
	        //Get each individual configuration
	        for (long j = 1 ; j < lNumConfigs+1 ; j++)
	        {
	           _bstr_t varTool;
	           _bstr_t varSwitch;
	           IConfigurationPtr pConfig;
	           _variant_t varj = j;
	
	           pConfig = pConfigs->Item(varj);
	
	           // Remove Preprocessor def for MFC DLL specifier, _AFXDLL
	           varTool   = "cl.exe";
	           varSwitch = "/D \"_AFXDLL\"";
	           pConfig->RemoveToolSettings(varTool, varSwitch, varj);
	
	           varTool   = "rc.exe";
	           varSwitch = "/d \"_AFXDLL\"";
	           pConfig->RemoveToolSettings(varTool, varSwitch, varj);
	
	           // OPTIONAL
	           // Add Libs that MFC headers would have pulled in automatically
	           // Feel free to customize this listing to your tastes
	           varTool = "link.exe";
	           varSwitch = "kernel32.lib user32.lib gdi32.lib winspool.lib "
	                       "comdlg32.lib advapi32.lib shell32.lib ole32.lib "
	                       "oleaut32.lib uuid.lib odbc32.lib odbccp32.lib";
	           pConfig->AddToolSettings(varTool, varSwitch, varj);
	        }
	     }
	
	Note that this code sample uses features from Visual C++ 5.0's new COM compiler
	support. The #import statement imports and creates definitions for all of the
	types in the DEVBLD.PKG type library. This allows the code to use the COM smart
	pointers of the form IInterfacePtr, as well as the new _bstr_t and _variant_t
	types. All of these new types automatically clean up used memory and release
	held interface pointers when they go out of scope.
	
	Also note that a standard Custom AppWizard uses a Precompiled header file,
	StdAfx.h. You should place the #import statement at the end of the #include list
	in StdAfx.h.
	
	NOTE: the path to DevBld.Pkg will be different if you are using Visual C++
	version 6.0. Assuming that Visual C++ version 6.0 was installed to the default
	directory on the C: drive, the #import statement should read as follows:
	
	     #import "C:\Program Files\Microsoft Visual Studio\Common\MsDev98\Bin\IDE\DevBld.Pkg"
	
	NOTE: The #import line above must be on the same line in your code.
	
	Refer to the Visual C++ documentation for more information.
	
	Caveats
	-------
	
	- Note that there is no programmatic method available for removing the internal
	  project setting that controls the "Microsoft Foundation Classes" setting on
	  the General Project Settings tab. Projects that are generated by custom
	  wizards that include the code above will still appear to "Use MFC in a Shared
	  DLL." The only way you can change this setting is by making unsupported
	  modifications to the .dsp project settings file. However, this setting is
	  only used by certain DevStudio MFC user interface elements, such as Class
	  Wizard and some MFC-based component gallery components. It should have no
	  effect on a non-MFC project.
	
	
	- Even after modifying project settings using AddToolSettings and
	  RemoveToolSettings as above, DEFAULT project settings will still remain the
	  same in Visual C++ version 5.0. If the user of a project generated by this
	  custom AppWizard opens up Project Settings and clicks Reset, the restored
	  project settings will include the removed MFC references. Again, the only way
	  to prevent this is to make unsupported changes to the generated .dsp project
	  settings file by hand after the custom AppWizard has created the project.
	
	  Visual C++ version 6.0 provides a new automation method that changes the
	  DEFAULT project settings. The Configuration object supports the
	  MakeCurrentSettingsDefault method. This method changes the configuration's
	  DEFAULT project settings to become the current settings.
	
	
	
	- When you use RemoveToolSettings, remove only one tool setting at a time. In
	  the example above, make another call to RemoveToolSettings to remove another
	  preprocessor definition from the CL.EXE command line rather than tacking the
	  definition to be removed onto the end of the same varSwitch statement. Also,
	  keep in mind that tool settings are case- sensitive, that is "/d" and "/D"
	  are not the same thing.
	
	- Unfortunately, AddToolSettings, RemoveToolSettings, and AddCustomBuildStep
	  (another IConfiguration method) operate on the entire project only in Visual
	  C++ version 5.0; they cannot make tool settings or create custom build steps
	  for a single file. For example, it is usually desirable to add a custom build
	  step for a project's IDL file to process the file using MIDL and generate TLB
	  and other necessary project files. The Developer Studio 97 object model does
	  not support this. Custom build steps for single files will have to be added
	  by hand after the custom AppWizard generates the projects.
	
	  The Visual C++ version 6.0 object model does support methods to change file
	  settings and add custom build steps for files. See the Visual C++ version 6.0
	  documentation on the following methods for the Configuration object :
	
	  AddFileSettings
	  RemoveFileSettings
	  AddCustomBuildStepToFile
	
	REFERENCES
	==========
	
	In the Visual C++ Online Help Index:
	
	- Automating Tasks In Developer Studio
	
	- Custom AppWizards
	
	- COM Support
	
	(c) Microsoft Corporation 1999, All Rights Reserved.
	Contributions by Jason Strayer, Microsoft Corporation
	
	
	======================================================================
	Keywords          : kbcode kbwizard kbVC500 
	Technology        : kbVCsearch kbAudDeveloper kbAppWizard
	Version           : WINNT:5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
