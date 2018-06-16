# Credit Card Leak

![](./img/1.png#center)

The given file is containing 403947 cards number. Let’s find which one is invalid with some python.

```python
def card(number):
	sum = 0
	num_digits = len(number)
	oddeven = num_digits & 1

	for count in range(0, num_digits):
		digit = int(number[count])

		if not (( count & 1 ) ^ oddeven ):
			digit = digit * 2
		if digit > 9:
			digit = digit - 9

		sum = sum + digit
	return  ((sum % 10) == 0)

f = open("cc_leak.txt.eecc6f896436", 'r')

for x in f:
	if not card(x.strip()):
		print(x.strip())
```

Launch the script and get the flag :

![](./img/2.png#center)

**The flag : 8692015931457397**