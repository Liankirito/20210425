# 2021.4/25 資安深耕營

## 上課筆記

### 異常處理
``` python
try:
        #會將try全部跑過一次，若發現異常(語法錯誤)會跳到except
except:
        #發現異常後需要執行的程式碼
```

## 解題紀錄
### 第一堂base64編碼 - 20 pts
``` python
import base64         //import base64的套件

base64.b64encode(b"BreakallCTF{happyhackinghighhaaha}")         //編碼

b'QnJlYWthbGxDVEZ7aGFwcHloYWNraW5naGlnaGhhYWhhfQ=='
>>> KeyboardInterrupt
```

### Base64 - 20 pts

``` python
import base64

base64.b64decode(b"QnJlYWtBTExDVEZ7NTN1c1pRM2hXVzI1ZGNoWjdkWGV9")

b'BreakALLCTF{53usZQ3hWW25dchZ7dXe}'
>>> KeyboardInterrupt
```

### Ascii - 20 pts
``` python
passWord = [66,114,101,97,107,65,76,76,67,84,70,123,65,109,118,48,117,68,121,101,114,118,80,116,109,86,114,57,83,83,83,75,125]        //寫一個list

for i in passWord:        //迴圈，使ascii碼轉換為符號
 print(chr(i),end='')

...
BreakALLCTF{Amv0uDyervPtmVr9SSSK}>>> 
KeyboardInterrupt
```

### Base32 - 20 pts
``` python
import base64

base64.b32decode(b'IJZGKYLLIFGEYQ2UIZ5TS6BUHA2VMUZXO5UWS5CCLJMFKVLIJVSX2===')

b'BreakALLCTF{9x485VS7wiitBZXUUhMe}'
>>> KeyboardInterrupt
```

### Morse code - 20 pts
線上解碼:INFOSECFLAGISMORSING 

### hello world - 50 pts
``` python
nc 120.114.62.214 2405        //連到伺服器
```

### 3rd - 50 pts
``` python
from pwn import *

ip = "120.114.62.214"
port = 2400

r = remote(ip, port)

r.recvuntil("Now You Turn")
r.recvuntil(" : ")
res = r.recvline()[:-1]        //不輸出患行符號
res = list(map(int,res.split()))        //抽取元素轉換list
res.sort() //排序list
print(res[-3])        //輸出第三大的數字

r.interactive()
```

### count - 50 pts

``` python
from pwn import *

ip = "120.114.62.214"
port = 2403

r = remote(ip, port)

r.recvuntil("wave")
r.recvuntil("?")
for i in range(1,101,1):	
	r.sendline(str(i))        //從1跑到100

r.interactive()
```
