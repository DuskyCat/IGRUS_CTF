# Inside
- - - -

* main
```
	 0x400596 <main>       push   rbp
   0x400597 <main+1>     mov    rbp, rsp
   0x40059a <main+4>     sub    rsp, 0x20
   0x40059e <main+8>     mov    rax, qword ptr fs:[0x28]
   0x4005a7 <main+17>    mov    qword ptr [rbp - 8], rax
   0x4005ab <main+21>    xor    eax, eax
   0x4005ad <main+23>    movabs rax, 0x77336e7b67616c66
   0x4005b7 <main+33>    mov    qword ptr [rbp - 0x20], rax
   0x4005bb <main+37>    movabs rax, 0x337633725f333162
   0x4005c5 <main+47>    mov    qword ptr [rbp - 0x18], rax
   0x4005c9 <main+51>    mov    dword ptr [rbp - 0x10], 0x72337372

   0x4005d0 <main+58>    mov    word ptr [rbp - 0xc], 0x7d21
   0x4005d6 <main+64>    mov    byte ptr [rbp - 0xa], 0
   0x4005da <main+68>    mov    edi, 0x400688
   0x4005df <main+73>    call   puts@plt <0x400460>
 
   0x4005e4 <main+78>    mov    eax, 0
   0x4005e9 <main+83>    mov    rdx, qword ptr [rbp - 8]
   0x4005ed <main+87>    xor    rdx, qword ptr fs:[0x28]
   0x4005f6 <main+96>    je     main+103 <0x4005fd>
 
   0x4005f8 <main+98>    call   __stack_chk_fail@plt <0x400470>
 
   0x4005fd <main+103>    leave  
   0x4005fe <main+104>    ret
```

어떤값을 스택에 쌓는 것을 볼 수 있다. 
스택을 비우기 전에 스택에 넣은 값을 보면

* rsp
```
00:0000│ rsp  0x7fffffffe140 ◂— 'flag{n3wb13_r3v3rs3r!}'
01:0008│      0x7fffffffe148 ◂— 'b13_r3v3rs3r!}'
02:0010│      0x7fffffffe150 ◂— 0x7d2172337372 /* 'rs3r!}' */
03:0018│      0x7fffffffe158 ◂— 0xe7e3d1ca98b96a00
```

플래그를 저장한걸 확인 할 수 있다.


## flag
- - - -
flag{n3wb13_r3v3rs3r!}



#IGRUS_CTF #IGRUS_CTF/Reversing