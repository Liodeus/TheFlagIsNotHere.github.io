# The Oracle

![](./img/1.png#center)

Let’s have a look at this note :

![](./img/2.png#center)

We have a gibberish note !

My first thought was to use xortool :

```
xortool -b emsg.txt
```
Go to the result folder, and search for the flag :

```
strings *|grep sctf{
```
![](./img/3.png#center)

That it we got it !

> Flag : sctf{W1ll_U_571ll_du_4ll_0f_7h1s_1f_1_h4d_n07_s41d_4ny7h1ng?}