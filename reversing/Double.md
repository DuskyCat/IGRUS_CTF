# Double
- - - -

* main
```
	 0x400710 <main>          push   rbp
   0x400711 <main+1>        mov    rbp, rsp
   0x400714 <main+4>        sub    rsp, 0x40
   0x400718 <main+8>        mov    rax, qword ptr fs:[0x28]
   0x400721 <main+17>       mov    qword ptr [rbp - 8], rax
   0x400725 <main+21>       xor    eax, eax

   0x400727 <main+23>    mov    qword ptr [rbp - 0x30], 0
   0x40072f <main+31>    mov    qword ptr [rbp - 0x28], 0
   0x400737 <main+39>    mov    qword ptr [rbp - 0x20], 0
   0x40073f <main+47>    mov    qword ptr [rbp - 0x18], 0
   0x400747 <main+55>    mov    qword ptr [rbp - 0x38], 0
   0x40074f <main+63>    mov    esi, 0x400884
   0x400754 <main+68>    mov    edi, 0x400887
   0x400759 <main+73>    call   fopen@plt <0x400590>
 
   0x40075e <main+78>    mov    qword ptr [rbp - 0x38], rax
   0x400762 <main+82>    mov    rdx, qword ptr [rbp - 0x38]
   0x400766 <main+86>    lea    rax, [rbp - 0x30]

   0x40076a <main+90>    mov    rcx, rdx
   0x40076d <main+93>    mov    edx, 0x1b
   0x400772 <main+98>    mov    esi, 1
   0x400777 <main+103>    mov    rdi, rax
   0x40077a <main+106>    call   fread@plt <0x400540>
 
   0x40077f <main+111>    mov    rax, qword ptr [rbp - 0x38]
   0x400783 <main+115>    mov    rdi, rax
   0x400786 <main+118>    call   fclose@plt <0x400550>
 
   0x40078b <main+123>    lea    rax, [rbp - 0x30]
   0x40078f <main+127>    mov    rdi, rax
   0x400792 <main+130>    call   encrypt <0x4006b6>

   0x400797 <main+135>    mov    esi, 0x400890
   0x40079c <main+140>    mov    edi, 0x400893
   0x4007a1 <main+145>    call   fopen@plt <0x400590>
 
   0x4007a6 <main+150>    mov    qword ptr [rbp - 0x38], rax
   0x4007aa <main+154>    lea    rax, [rbp - 0x30]
   0x4007ae <main+158>    mov    rdi, rax
   0x4007b1 <main+161>    call   strlen@plt <0x400560>
 
   0x4007b6 <main+166>    mov    rsi, rax
   0x4007b9 <main+169>    mov    rdx, qword ptr [rbp - 0x38]
   0x4007bd <main+173>    lea    rax, [rbp - 0x30]
   0x4007c1 <main+177>    mov    rcx, rdx

   0x4007c4 <main+180>    mov    rdx, rsi
   0x4007c7 <main+183>    mov    esi, 1
   0x4007cc <main+188>    mov    rdi, rax
   0x4007cf <main+191>    call   fwrite@plt <0x4005a0>
 
   0x4007d4 <main+196>    mov    rax, qword ptr [rbp - 0x38]
   0x4007d8 <main+200>    mov    rdi, rax
   0x4007db <main+203>    call   fclose@plt <0x400550>
 
   0x4007e0 <main+208>    mov    eax, 0
   0x4007e5 <main+213>    mov    rcx, qword ptr [rbp - 8]
   0x4007e9 <main+217>    xor    rcx, qword ptr fs:[0x28]
   0x4007f2 <main+226>    je     main+233 <0x4007f9>

   0x4007f4 <main+228>    call   __stack_chk_fail@plt <0x400570>
 
   0x4007f9 <main+233>    leave  
   0x4007fa <main+234>    ret
```

* encrypt
```
	 0x4006b6 <encrypt>       push   rbp
   0x4006b7 <encrypt+1>     mov    rbp, rsp
   0x4006ba <encrypt+4>     push   rbx
   0x4006bb <encrypt+5>     sub    rsp, 0x28
   0x4006bf <encrypt+9>     mov    qword ptr [rbp - 0x28], rdi
   0x4006c3 <encrypt+13>    mov    dword ptr [rbp - 0x14], 0
   0x4006ca <encrypt+20>    jmp    encrypt+59 <0x4006f1>
 
   0x4006cc <encrypt+22>    mov    eax, dword ptr [rbp - 0x14]
   0x4006cf <encrypt+25>    movsxd rdx, eax
   0x4006d2 <encrypt+28>    mov    rax, qword ptr [rbp - 0x28]
   0x4006d6 <encrypt+32>    add    rax, rdx

   0x4006d9 <encrypt+35>    mov    edx, dword ptr [rbp - 0x14]
   0x4006dc <encrypt+38>    movsxd rcx, edx
   0x4006df <encrypt+41>    mov    rdx, qword ptr [rbp - 0x28]
   0x4006e3 <encrypt+45>    add    rdx, rcx
   0x4006e6 <encrypt+48>    movzx  edx, byte ptr [rdx]
   0x4006e9 <encrypt+51>    add    edx, edx
   0x4006eb <encrypt+53>    mov    byte ptr [rax], dl
   0x4006ed <encrypt+55>    add    dword ptr [rbp - 0x14], 1
   0x4006f1 <encrypt+59>    mov    eax, dword ptr [rbp - 0x14]
   0x4006f4 <encrypt+62>    movsxd rbx, eax
   0x4006f7 <encrypt+65>    mov    rax, qword ptr [rbp - 0x28]

   0x4006fb <encrypt+69>    mov    rdi, rax
   0x4006fe <encrypt+72>    call   strlen@plt <0x400560>
 
   0x400703 <encrypt+77>    cmp    rbx, rax
   0x400706 <encrypt+80>    jb     encrypt+22 <0x4006cc>
 
   0x400708 <encrypt+82>    nop    
   0x400709 <encrypt+83>    add    rsp, 0x28
   0x40070d <encrypt+87>    pop    rbx
   0x40070e <encrypt+88>    pop    rbp
   0x40070f <encrypt+89>    ret 
```


flag.txt파일에 있는 값을 byte단위로 2배씩 상승 시켜서 flag.enc에 저장하는 코드이다.
flag.enc파일이 주어졌으니 이를 복호화 하면 될것 같다.
flag.enc파일의 hex값은

* flag.enc
```
CC D8 C2 CE F6 C8 60 EA C4 D8 66 C8 BE 68 E6 C6 62 62 BE EC 68 D8 EA 66 42 FA 14
```

이 값을 byte단위로 2를 나눈다

* Dec
```
66 6c 61 67 7b 64 30 75 62 6c 33 64 5f 34 73 63 31 31 5f 76 34 6c 75 33 21 7d 0a
```

이를 ascii코드로 변환하면 플래그가 된다.


## flag
- - - -
flag{d0ubl3d_4sc11_v4lu3!}



#IGRUS_CTF #IGRUS_CTF/Reversing