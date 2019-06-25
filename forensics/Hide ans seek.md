# Hide ans seek
- - - -

* Place.hwp
![](Hide%20ans%20seek/%E1%84%8F%E1%85%A2%E1%86%B8%E1%84%8E%E1%85%A5.png)

hwp파일을 hxd로 확인해보니 마지막에 png파일의 trailer가 있었다.
png 파일일 것이라 생각되어 png 파일의 siniture 코드인 89 50 4E 47 0D 0A 1A 0A 를 찾아보니 중간에 있었고, 위쪽의 데이터를 없애고 png파일을 만들어보니 플래그가 담겨있었다.

* flag.png
![](Hide%20ans%20seek/test.png)


## flag
- - - -
flag{h1dd3n_f1l3_1n_hwp}



#IGRUS_CTF #IGRUS_CTF/Forensics