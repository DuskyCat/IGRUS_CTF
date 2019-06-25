# Secret
- - - -

* main
```
   0x4006f6 <main>       push   rbp
   0x4006f7 <main+1>     mov    rbp, rsp
   0x4006fa <main+4>     sub    rsp, 0x100
   0x400701 <main+11>    mov    rax, qword ptr [rip + 0x200960] <0x601068>
   0x400708 <main+18>    mov    esi, 0
   0x40070d <main+23>    mov    rdi, rax
   0x400710 <main+26>    call   setbuf@plt <0x400590>
 
   0x400715 <main+31>    mov    edi, 0x400814
   0x40071a <main+36>    mov    eax, 0
   0x40071f <main+41>    call   printf@plt <0x4005b0>
 
   0x400724 <main+46>    lea    rax, [rbp - 0x100]

   0x40072b <main+53>    mov    rsi, rax
   0x40072e <main+56>    mov    edi, 0x40082b
   0x400733 <main+61>    mov    eax, 0
   0x400738 <main+66>    call   __isoc99_scanf@plt <0x4005e0>
 
   0x40073d <main+71>    lea    rax, [rbp - 0x100]
   0x400744 <main+78>    mov    esi, secret <0x601060>
   0x400749 <main+83>    mov    rdi, rax
   0x40074c <main+86>    call   strcmp@plt <0x4005d0>
 
   0x400751 <main+91>    test   eax, eax
   0x400753 <main+93>    jne    main+122 <0x400770>
 
   0x400755 <main+95>    mov    edi, 0x400831

   0x40075a <main+100>    call   puts@plt <0x400580>
 
   0x40075f <main+105>    mov    edi, 0x40084a
   0x400764 <main+110>    mov    eax, 0
   0x400769 <main+115>    call   system@plt <0x4005a0>
 
   0x40076e <main+120>    jmp    main+132 <0x40077a>
 
   0x400770 <main+122>    mov    edi, 0x400857
   0x400775 <main+127>    call   puts@plt <0x400580>
 
   0x40077a <main+132>    mov    eax, 0
   0x40077f <main+137>    leave  
   0x400780 <main+138>    ret   
```


* call secret
```
pwndbg> x/10x 0x601060
0x601060 <secret>:	0xdeadbeef	0x00000000	0xf7fa6760	0x00007fff
```

secret에는 0xdeadbeef 가 들어있고 이 값과 입력된 값을 비교해서 같으면 system 함수를 출력하는 코드이다.
버퍼를 100h(256바이트)을 만들었고, scanf 를 %256s 로 지정해서 256개의 캐릭터를 받게 하여 오버플로우를 막고있다.


## exploit
- - - -
```
root@kali:~/Desktop/igrusCTF/pwn/secret# (python -c 'print "\xef\xbe\xad\xde"') | nc igrus.cf 8101
Give me secret code > Good job!, Here is flag.
flag{c4n_y0u_s3nd_n0n_pr1nt4bl3_c0d3?}
```


## flag
- - - -
flag{c4n_y0u_s3nd_n0n_pr1nt4bl3_c0d3?}



#IGRUS_CTF #IGRUS_CTF/Pwnable