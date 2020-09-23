<div align="center">

## Inline assembly example


</div>

### Description

This code shows how to write in-line assembly in C\C++. I tried it with MVC 6.0, but I'm almost convinced that it'll work with other compilers.

Generaly, the assembly procedure takes a WORD (16 bits \ 2 bytes) and replaces the upper byte with the lower (not special, I know, but a good example of somthing hard to do without ASM).

P L E A S E comment & vote, even if you dislike.
 
### More Info
 
No inputs.

Tested on MVC 6, windows XP, Pentium 4 1.80GHz.

Returns some values & their values after upper-lower byte swap.

Also returns the assembly code (prints it to the screen).

No side effects.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[OR13](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/or13.md)
**Level**          |Intermediate
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+
**Category**       |[Algorithms](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/algorithms__3-29.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/or13-inline-assembly-example__3-6577/archive/master.zip)





### Source Code

```
#include <iostream.h>
int SwapLowHigh(int num)
{
	int retu;
	_asm
	{
		mov edx,num
		xor eax,eax		;//clear eax. why? because later we'll return eax instead of only ax...
		mov ax,dx		;//until now it was just prepare. now it beggins
		mov dl,al		;//dl acts like 'temp'
		mov al,ah		;//swap
		mov ah,dl
		mov retu,eax	;//return the value in eax (actually in ax, the first word is cleaned)
	}
	return retu;
}
int main()
{
	cout<<"SwapLowHigh(1):\t\t"<<SwapLowHigh(1)<<"\n"; //print for example "SwapLowHigh(16): 4096"
	cout<<"SwapLowHigh(2):\t\t"<<SwapLowHigh(2)<<"\n";
	cout<<"SwapLowHigh(4):\t\t"<<SwapLowHigh(4)<<"\n";
	cout<<"SwapLowHigh(8):\t\t"<<SwapLowHigh(8)<<"\n";
	cout<<"SwapLowHigh(16):\t"<<SwapLowHigh(16)<<"\n";
	cout<<"SwapLowHigh(32):\t"<<SwapLowHigh(32)<<"\n";
	cout<<"SwapLowHigh(64):\t"<<SwapLowHigh(64)<<"\n";
	cout<<"SwapLowHigh(128):\t"<<SwapLowHigh(128)<<"\n";
	cout<<"SwapLowHigh(256):\t"<<SwapLowHigh(256)<<"\n";
	cout<<"SwapLowHigh(512):\t"<<SwapLowHigh(512)<<"\n";
	cout<<"SwapLowHigh(1024):\t"<<SwapLowHigh(1024)<<"\n";
	cout<<"SwapLowHigh(2048):\t"<<SwapLowHigh(2048)<<"\n";
	cout<<"SwapLowHigh(4096):\t"<<SwapLowHigh(4096)<<"\n";
	cout<<"SwapLowHigh(8192):\t"<<SwapLowHigh(8192)<<"\n";
	cout<<"SwapLowHigh(16384):\t"<<SwapLowHigh(16384)<<"\n";
	cout<<"SwapLowHigh(32768):\t"<<SwapLowHigh(32768)<<"\n\n\n";
	cout<<"Code:\n\n";		//print the assembly code
	cout<<"int SwapLowHigh(int num)\n{\n\tint retu;\n\t_asm\n\t{\n";
	cout<<"\t\tmov edx,num\n\t\txor eax,eax\t\t;//later returned instead of ax.\n";
	cout<<"\t\tmov ax,dx\t\t;//until now it was just prepare.\n";
	cout<<"\n\t\tmov dl,al\t\t;//dl acts like 'temp'\n\t\tmov al,ah\t\t;//swap\n";
	cout<<"\t\tmov ah,dl\n\n\t\tmov retu,eax\t\t;//eax is integer, ax is word\n";
	cout<<"\t}\n\treturn retu;\n}\n\n";
	return 0;
}
```

