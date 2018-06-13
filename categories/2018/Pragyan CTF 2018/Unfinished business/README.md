# Unfinished business

![](./img/1.png#center)

Open the link and you got this :

![](./img/2.png#center)

Connect with your credentials and you get redirect on this page (/unavailable.php).

![](./img/3.png#center)

Let’s try to connect via curl and see what happened :


![](./img/4.png#center)

As you can see the location is /admin.php but we are redirect on /unavailable.php. Let’s try to go on /admin.php with curl using our PHPSESSID to stay connected.

![](./img/5.png#center)

**The Flag : pctf{y0u=Sh0Uldn’1/h4v3*s33n,1his. : )}**