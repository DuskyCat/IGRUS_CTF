# Login & Login Secured
- - - -

* main
```
	 0x400812 <main>       push   rbp
   0x400813 <main+1>     mov    rbp, rsp
   0x400816 <main+4>     sub    rsp, 0x50
   0x40081a <main+8>     mov    rax, qword ptr fs:[0x28]
   0x400823 <main+17>    mov    qword ptr [rbp - 8], rax
   0x400827 <main+21>    xor    eax, eax
   0x400829 <main+23>    mov    edi, 0x40094f
   0x40082e <main+28>    mov    eax, 0
   0x400833 <main+33>    call   printf@plt <0x4005a0>
 
   0x400838 <main+38>    lea    rax, [rbp - 0x50]
   0x40083c <main+42>    mov    rsi, rax

   0x40083f <main+45>    mov    edi, 0x400955
   0x400844 <main+50>    mov    eax, 0
   0x400849 <main+55>    call   __isoc99_scanf@plt <0x4005c0>
 
   0x40084e <main+60>    mov    edi, 0x400958
   0x400853 <main+65>    mov    eax, 0
   0x400858 <main+70>    call   printf@plt <0x4005a0>
 
   0x40085d <main+75>    lea    rax, [rbp - 0x30]
   0x400861 <main+79>    mov    rsi, rax
   0x400864 <main+82>    mov    edi, 0x400955
   0x400869 <main+87>    mov    eax, 0
   0x40086e <main+92>    call   __isoc99_scanf@plt <0x4005c0>

   0x400873 <main+97>    lea    rdx, [rbp - 0x30]
   0x400877 <main+101>    lea    rax, [rbp - 0x50]
   0x40087b <main+105>    mov    rsi, rdx
   0x40087e <main+108>    mov    rdi, rax
   0x400881 <main+111>    call   check <0x4007bf>
 
   0x400886 <main+116>    mov    eax, 0
   0x40088b <main+121>    mov    rcx, qword ptr [rbp - 8]
   0x40088f <main+125>    xor    rcx, qword ptr fs:[0x28]
   0x400898 <main+134>    je     main+141 <0x40089f>
 
   0x40089a <main+136>    call   __stack_chk_fail@plt <0x400590>
 
   0x40089f <main+141>    leave  

   0x4008a0 <main+142>    ret 
```

* check
```
	 0x4007bf <check>       push   rbp
   0x4007c0 <check+1>     mov    rbp, rsp
   0x4007c3 <check+4>     sub    rsp, 0x10
   0x4007c7 <check+8>     mov    qword ptr [rbp - 8], rdi
   0x4007cb <check+12>    mov    qword ptr [rbp - 0x10], rsi
   0x4007cf <check+16>    mov    rax, qword ptr [rbp - 8]
   0x4007d3 <check+20>    mov    rdi, rax
   0x4007d6 <check+23>    call   check_id <0x4006d6>
 
   0x4007db <check+28>    test   eax, eax
   0x4007dd <check+30>    je     check+70 <0x400805>
 
   0x4007df <check+32>    mov    rax, qword ptr [rbp - 0x10]

   0x4007e3 <check+36>    mov    rdi, rax
   0x4007e6 <check+39>    call   check_password <0x40074a>
 
   0x4007eb <check+44>    test   eax, eax
   0x4007ed <check+46>    je     check+70 <0x400805>
 
   0x4007ef <check+48>    mov    edi, 0x400934
   0x4007f4 <check+53>    call   puts@plt <0x400570>
 
   0x4007f9 <check+58>    mov    edi, flag <0x601060>
   0x4007fe <check+63>    call   puts@plt <0x400570>
 
   0x400803 <check+68>    jmp    check+80 <0x40080f>
 
   0x400805 <check+70>    mov    edi, 0x400942
   0x40080a <check+75>    call   puts@plt <0x400570>

   0x40080f <check+80>    nop    
   0x400810 <check+81>    leave  
   0x400811 <check+82>    ret 
```

코드 구성이 main에서 id와 pw를 입력받고 check함수에 이 값을 넘겨 준다.
이후 check함수에서는 check_id와 check_pw함수를 호출해서 이 함수에 저장되어 있는 값과 입력받은 값을 비교한다.

* check_id
```
	 0x4006d6 <check_id>       push   rbp
   0x4006d7 <check_id+1>     mov    rbp, rsp
   0x4006da <check_id+4>     sub    rsp, 0x20
   0x4006de <check_id+8>     mov    qword ptr [rbp - 0x18], rdi
   0x4006e2 <check_id+12>    mov    rax, qword ptr fs:[0x28]
   0x4006eb <check_id+21>    mov    qword ptr [rbp - 8], rax
   0x4006ef <check_id+25>    xor    eax, eax
   0x4006f1 <check_id+27>    mov    dword ptr [rbp - 0x10], 0x6277656e
   0x4006f8 <check_id+34>    mov    word ptr [rbp - 0xc], 0x6569
   0x4006fe <check_id+40>    mov    byte ptr [rbp - 0xa], 0
   0x400702 <check_id+44>    lea    rax, [rbp - 0x10]

   0x400706 <check_id+48>    mov    rdi, rax
   0x400709 <check_id+51>    call   strlen@plt <0x400580>
 
   0x40070e <check_id+56>    mov    rdx, rax
   0x400711 <check_id+59>    mov    rcx, qword ptr [rbp - 0x18]
   0x400715 <check_id+63>    lea    rax, [rbp - 0x10]
   0x400719 <check_id+67>    mov    rsi, rcx
   0x40071c <check_id+70>    mov    rdi, rax
   0x40071f <check_id+73>    call   strncmp@plt <0x400560>
 
   0x400724 <check_id+78>    test   eax, eax
   0x400726 <check_id+80>    jne    check_id+89 <0x40072f>
 
   0x400728 <check_id+82>    mov    eax, 1

   0x40072d <check_id+87>    jmp    check_id+94 <0x400734>
 
   0x40072f <check_id+89>    mov    eax, 0
   0x400734 <check_id+94>    mov    rsi, qword ptr [rbp - 8]
   0x400738 <check_id+98>    xor    rsi, qword ptr fs:[0x28]
   0x400741 <check_id+107>    je     check_id+114 <0x400748>
 
   0x400743 <check_id+109>    call   __stack_chk_fail@plt <0x400590>
 
   0x400748 <check_id+114>    leave  
   0x400749 <check_id+115>    ret 
```

rax에 저장해둔 값을 넣어 둔다. 
```
02:0010│ rax  0x7fffffffe0d0 ◂— 0x65696277656e /* 'newbie' */
```


* check_pwassword
```
	 0x40074a <check_password>       push   rbp
   0x40074b <check_password+1>     mov    rbp, rsp
   0x40074e <check_password+4>     sub    rsp, 0x30
   0x400752 <check_password+8>     mov    qword ptr [rbp - 0x28], rdi
   0x400756 <check_password+12>    mov    rax, qword ptr fs:[0x28]
   0x40075f <check_password+21>    mov    qword ptr [rbp - 8], rax

   0x400763 <check_password+25>    xor    eax, eax
   0x400765 <check_password+27>    movabs rax, 0x6472307773734070
   0x40076f <check_password+37>    mov    qword ptr [rbp - 0x20], rax
   0x400773 <check_password+41>    mov    byte ptr [rbp - 0x18], 0
   0x400777 <check_password+45>    lea    rax, [rbp - 0x20]

   0x40077b <check_password+49>    mov    rdi, rax
   0x40077e <check_password+52>    call   strlen@plt <0x400580>
 
   0x400783 <check_password+57>    mov    rdx, rax
   0x400786 <check_password+60>    mov    rcx, qword ptr [rbp - 0x28]
   0x40078a <check_password+64>    lea    rax, [rbp - 0x20]
   0x40078e <check_password+68>    mov    rsi, rcx

   0x400791 <check_password+71>    mov    rdi, rax
   0x400794 <check_password+74>    call   strncmp@plt <0x400560>
 
   0x400799 <check_password+79>    test   eax, eax
   0x40079b <check_password+81>    jne    check_password+90 <0x4007a4>
 
   0x40079d <check_password+83>    mov    eax, 1
   0x4007a2 <check_password+88>    jmp    check_password+95 <0x4007a9>
 
   0x4007a4 <check_password+90>    mov    eax, 0
   0x4007a9 <check_password+95>    mov    rsi, qword ptr [rbp - 8]
   0x4007ad <check_password+99>    xor    rsi, qword ptr fs:[0x28]
   0x4007b6 <check_password+108>    je     check_password+115 <0x4007bd>
 
   0x4007b8 <check_password+110>    call   __stack_chk_fail@plt <0x400590>

   0x4007bd <check_password+115>    leave  
   0x4007be <check_password+116>    ret 
```

pw값을 rax에 넣어서 입력된 값과 비교한다.
```
02:0010│ rax  0x7fffffffe0c0 ◂— 'p@ssw0rd'
```


id=newbie
pw=p@ssw0rd

login파일을 실행 후 id와 pw를 입력하면 플래그가 나온다.


## flag
- - - -
* login
flag{ch3ck1ng_1s_n0t_m4tt3r}

* login secured
flag{ch3ck1ng_1s_m4tt3r_1n_th1s_c4s3}



#IGRUS_CTF #IGRUS_CTF/Reversing