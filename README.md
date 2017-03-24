There are probably better ways to do this but I just found this useful when doing various AV bypass and exploit dev activities.
It is just a shitload of NOPS to be used in as a "Canvas" to test instructions, shellcode etc while inside a debugger. 
The int3 breakpoint allows the developer to run the binary and find the startof the nops/canvas and set a breakpoint or find an address to jump to to start developing.

Uses:
Anything realy.
This can be used as a harmless looking "container" program to contain a backdoor, known malicious binary or your own custom shellcode. If built the right way AV won't detect it. 
I found this useful when trying to obfuscate known malware, for some reason the known malware files still got detetced by some AV's even after obfuscating every section that I could without breaking it. 
Binary pasting the shellcode of known malware inside this container along with an encoder stub and a few other mods managed to bypass signature detection and sandboxing. 

compile with:
nasm -f elf32 nops.asm
gcc -m32 nops.o -o nops.exe

Launch your choice of debugger, hit play and you should hit the breakpoint, from there you can test/develop code and step through it.