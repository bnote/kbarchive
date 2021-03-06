---
layout: page
title: "Q32892: Compiling with /Zi Causes Code Motion Optimization Suppression"
permalink: /kb/032/Q32892/
---

## Q32892: Compiling with /Zi Causes Code Motion Optimization Suppression

{% raw %}

	Article: Q32892
	Product(s): See article
	Version(s): 4.00 5.00 5.10 | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 19-JUL-1988
	
	Compiling with /Zi and no other switches causes certain code motion
	optimizations to be suppressed, i.e, the code generated for a program
	with the defaults and with /Zi may differ.
	   You can override this default behavior by explicitly specifying the
	default optimizations on the command line. For example, you can
	compile with the following command line to get the same code with or
	without /Zi:
	
	   cl /Zi /Ot file.c

{% endraw %}
