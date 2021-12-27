---
id: GNVXFys9GwyOlN36BGWaI
title: L4
desc: ''
updated: 1629778062997
created: 1629697052614
---

## Review

## Chap 10 AVR Timer Programming in C

![](/assets/images/2021-08-23-11-11-17.png)


Programs to Do:
![](/assets/images/2021-08-23-11-13-01.png)


Program for BCD to ASCII
(Author's Answer)
![](/assets/images/2021-08-23-11-13-19.png)


Question:
![](/assets/images/2021-08-23-11-15-40.png)

```
#include <avr/io.h>

int main() {
	unsigned int temp1 = 0x34;
	unsigned int temp2 = 0x37;
	DDRB = 0xFF;
	while (true) {
		unsigned int msb = temp1 & 0x0F;	//msb = 0x04
		unsigned int lsb = temp2 & 0x0F;	//lsb = 0x07 
		msb = msb << 4;	(4 or 1? what?)					//msb = 0x40
		PORTB = msb | lsb;					//0x40 | 0x07 = 0x47
	}
	return 0;
}
```
![](/assets/images/2021-08-23-11-37-43.png)


## AVR Timer (Chap 10)

Time Delays are necessary sometimes.

Inbuilt timers exist in AVR.

![](/assets/images/2021-08-23-11-40-11.png)


Eg. Timer Operation:
- Washing Machine waiting to dry clothes
- Microwave Oven, put timer 30 seconds and wait 30 seconds for food to cook

Eg. Counter Operation
ATM Machine withdraw 10k in 500 rupees notes (20 notes) - it must count how many notes are passing through it.

ATMega32 has three timers
- Timer 0 8 bit ( 00H to FFH )
- Timer 1 16 bit ( 000H to FFFFH )
- Timer 2 8 bit( 00H to FFH )

![](/assets/images/2021-08-23-11-47-11.png)

![](/assets/images/2021-08-23-11-54-29.png)

![](/assets/images/2021-08-23-11-57-30.png)

![](/assets/images/2021-08-23-12-00-18.png)

![](/assets/images/2021-08-23-12-02-06.png)

![](/assets/images/2021-08-23-12-04-29.png)

OCR 0(zero)
![](/assets/images/2021-08-23-12-05-47.png)

![](/assets/images/2021-08-23-12-15-24.png)

![](/assets/images/2021-08-23-12-20-18.png)
