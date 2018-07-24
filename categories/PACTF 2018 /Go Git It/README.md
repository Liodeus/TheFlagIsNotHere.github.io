# Go Git It

![](./img/1.png#center)

We are given a bz2 archive.

![](./img/2.png#center)

After extracting it’s content we obtain a git repository. From there I have run this command :

```
for f in .git/objects/*/*; do zlib-flate -uncompress < $f; done
```

And from that you can read the flag which is :

![](./img/3.png#center)