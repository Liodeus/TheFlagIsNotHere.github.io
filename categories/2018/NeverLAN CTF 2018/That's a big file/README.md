# That's a big file

![](./img/1.png#center)

File link : [Link](https://s3-us-west-2.amazonaws.com/neverlanctf/files/ThatsBig.zip.gz)

So we have a big file with compressed data. Lets see what’s inside. It looks like it’s a big base64 file.

So let’s try to decode it :

> cat ThatsBix.txt | base64 -d

Huum it’s still base64 but with less data. It looks like this is a file with multiple layers of base64.

Let’s write some python !

```python
import base64

flag = open("ThatsBig.txt", 'r').read()


for x in range(100):
    try:
        flag = base64.b64decode(flag).decode('utf-8')
    except:
        print(flag)
```

> The flag : flag{persistant_are_we?}