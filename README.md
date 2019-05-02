# c-inline-asm-stack-memory-listing 64-bit

Generic c program

List current function stack frame pointers

	* ask user for how many bytes to display

    * default to at least 64 bytes
	
    * use inline asm
    
    * anchor is rbp

The inline asm to obtain current function frame pointers is as follows:

Visual Studio 2017 with Intel C++ compiler 19.0
-----------------------------------------------
    __asm mov rbpVar, rbp;
  	__asm mov rspVar, rsp;

gcc compiler
-----------------------------------------------
    __asm__ (".intel_syntax; \n\t"
            "movq %0, %%rbp; \n\t"
            "movq %1, %%rsp; \n\t"
            ".att_syntax;"
            : "=r" (rbpVar), "=r" (rspVar));
