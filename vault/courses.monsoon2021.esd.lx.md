---
id: XzZQXuBYxUI2jCmxhHkPp
title: Lx
desc: ''
updated: 1631516071570
created: 1631511479812
---

Date: 13th September 2021

Lecture Number : Unknown

## Quick Revision

![](/assets/images/2021-09-13-11-15-36.png)


![](/assets/images/2021-09-13-11-21-29.png)

![](/assets/images/2021-09-13-11-25-19.png)


![](/assets/images/2021-09-13-11-43-22.png)

![](/assets/images/2021-09-13-11-45-59.png)

![](/assets/images/2021-09-13-11-48-16.png)


```c
#include <avr/io.h>
int main()
{
    DDRC=0xFF; // Output Mode 
    PORTB=0x00; // 0th bit of B 
    TCCR0=0x06; // Falling edge 

    while (1)
    {

    PORTC=TCNT0;
    }
    return 0;
}

```

![](/assets/images/2021-09-13-12-08-43.png)

```c
#include<avr/io.h>

void T0Delay() {
    TCNT0 = 0; // TCNT0 = 0
    OCR0 = 75; // OCR0 - TCNT0 = 75
    TCCR0 = 0x09; // CTC mode and no prescaling
    while( (TIFR & 0x2) == 0); // CHeck 1st bit
    TCCR0 = 0; // Stop clock
    TIFR = 0x2; // Reset
}

int main() {
    DDRA = 0x02;
    while(1) {
        PORTA = PORTA ^ 0x02;
        T0Delay();
    }
    return 0;
}

```