# Mr.reagan

![](./img/1.png#center)

First,Let’s take a look at the file :

![](./img/2.png#center)

After mounting this partition, and after using several tools to search the presence of a flag. I had to go back to the starting point.

I used ntfsundelete tool to see if there are any deleted files :

```
ntfsundelete mrreagan
```
Result :

![](./img/3.png#center)

As we can see there are several interesting files that we recovered.

```
ntfsundelete mrreagan -u -i **Inode**
```
Now that we have all the files we’ll look at what they contain:

**$Info : c2N0ZnszbD**  
**$Secure : NjdHIwbTRn**  
**$Boot : bjN0MWNfcH**  
**$Extend : VsNTNfdzRz**  
**$LogFile : X2Y0azN9Cg**  
**Morpheus.txt : This line is tapped, so I must be brief.**  
**Tank.txt : 73656366**  
**Dozer.txt : 73656366**  
**Trinity.txt : I was looking for an answer. It’s the question that drives us mad.**  
**Neo.txt : What is the Matrix.**  

My idea was then to paste all the pieces that looked like an encrypted message :

**c2N0ZnszbDNjdHIwbTRnbjN0MWNfcHVsNTNfdzRzX2Y0azN9Cg**

Try to decode this base64 :

![](./img/4.png#center)

> Flag : sctf{3l3ctr0m4gn3t1c_pul53_w4s_f4k3}