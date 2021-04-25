# python20210425
~~~python
from pwn import *

r = remote('140.110.112.22', 2402)

r.recvuntil('year :')
r.recvuntil('year :')

for i in range(1,101):
	r.recvuntil('year :')
	y = r.recvuntil('\n')
	y = y.decode()
	y = y.strip()
	y = int(y)
	
	if y%4 == 0 and not y%100 == 0:
		r.sendline(b'leap')
	elif y%400 == 0:
		r.sendline(b'leap')
	else:
		r.sendline(b'ordinary')

r.interactive()
~~~
