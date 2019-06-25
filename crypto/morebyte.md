# morebyte
- - - -

* enc
```
/+32($w f!s 1`;*e!t<6!07&dc':
```

* make.py
```
from flag import flag
from itertools import cycle

enc = ""
key = cycle('IGRUS')

for i,j in zip(flag, key):
	enc += chr(ord(i) ^ ord(j))

f = open('enc', 'wt')
f.write(enc)
f.close()
```

make.py 를 보면 flag 값을 IGRUS와 xor연산하여 암호화 한 뒤 enc에 저장한 것이다.
xor연산의 특징은 xor연산의 결과를 다시 xor 하면 원래의 값이 나온다는 것이다.
그래서 복호화를 하는 간단한 프로그램을 만든뒤 실행하여 값을 출력하게 하였다.


* dec.py
```
from itertools import cycle

dec = ""
key = cycle('IGRUS')
flag = "/+32($w f!s 1`;*e!t<6!07&dc':"

for i,j in zip(flag, key):
    dec += chr(ord(i) ^ ord(j))

print(dec)
```



## flag
- - - -
flag{m0r3_h4rd3r_x0r_3ncrypt10n}



#IGRUS_CTF #IGRUS_CTF/Crypto