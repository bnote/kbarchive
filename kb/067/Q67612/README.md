---
layout: page
title: "Q67612: Bad Code Generated for Function Returning _self Based Pointer"
permalink: /kb/067/Q67612/
---

## Q67612: Bad Code Generated for Function Returning _self Based Pointer

{% raw %}

	Article: Q67612
	Product(s): See article
	Version(s): 6.00 6.00a | 6.00 6.00a
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist6.00 buglist6.00a | mspl13_c
	Last Modified: 30-JAN-1991
	
	The C versions 6.00 and 6.00a compilers will generate incorrect code
	for a function that returns a pointer based on self. The code
	generated for the return statement introduces an extra level of
	indirection.
	
	Microsoft has confirmed this to be a problem in C versions 6.00 and
	6.00a. We are researching this problem and will post new information
	here as it becomes available.
	
	The following program fragment demonstrates this problem. Compile the
	code with the /Fc option to generate an assembly listing, and observe
	the code in the resulting .COD file for the return statement in the
	function test().
	
	struct foo {
	            int  _based((_segment) _self) *pbs;
	           } far *pfoo;
	
	int far *test(void)
	{
	   return(pfoo->pbs);
	}

{% endraw %}
