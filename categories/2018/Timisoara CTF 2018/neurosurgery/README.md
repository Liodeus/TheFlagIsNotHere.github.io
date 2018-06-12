# Neurosurgery

![](./img/1.png#center)

So we are given a zip containing a large file name image (2,1G). Look like a memory dump. Let’s find out with volatility what kind of dump we have.

![](./img/2.png#center)

So this is not a windows dump. Linux maybe ?

![](./img/3.png#center)

Linux it is ! So now we need a profil to work with volatility on it. Let’s make it.

First I downloaded an Ubuntu version 16.04.4 [Link](https://www.ubuntu.com/download/desktop), then run virtualbox with this iso, install it and use these commands :


```
apt-get install dwarfdump build-essential linux-headers-4.4.0-116-generic volatility zip
cd /usr/share/volatility/tools/linux/
make
zip /home/Profil.zip ./module.dwarf /boot/System.map-4.4.0-116-generic
```

After that you take the zip file and place it here : /usr/lib/python2.7/dist-packages/volatility/plugins/overlays/linux/

Your profil is now ready ! First I want to see if there was some commands left.

![](./img/4.png#center)

And there is ! So as you can see there is something weird going on with ht0p, why not dump it to see what it does ?

![](./img/5.png#center)

![](./img/6.png#center)

![](./img/7.png#center)

And there you have the flag : timctf{ch4nc3_f4vors_th3_pr3p4red_m1nd}