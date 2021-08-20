---
id: ZAnOfd2gZ6LnhhkBZxhmE
title: L3
desc: ''
updated: 1629447758733
created: 1629437919229
---

### Selection Criteria for choosing a microcontroller

![](/assets/images/2021-08-20-11-25-28.png)

1. Effectively meeting computing needs
* 8 Bit vs 16 Bit vs 32 Bit controller
* Speed
* Power Consumption
* Packaging
    * Space
    * Assembling
    * Prototyping End Product
* RAM and ROM on chip
* No. of I/O pins
* No of timers 
* How frequent are updates 
* Cost per unit

2. Availability of Software Dev Tools
* Ease of development of a product around it
    * Key considerations of Availability of
        * Assemblers
        * Debugger
        * Code-efficient C-language compiler
        * Tech Support
        * In-house and Outside expertise 

3. Availability of Reliable Sources of uC
* Companies supplying this controller
* Are the companies reliable


Course Microcontrollers
8051 <> PIC <> AVR
![](/assets/images/2021-08-20-11-36-55.png) 


### AVR Microcontrollers

Harvard | Princeton
---|---
Two different memory interfaces |Single memory interface
![](/assets/images/2021-08-20-11-43-46.png) | ![](/assets/images/2021-08-20-11-42-52.png)


CISC vs RISC Procesors

CISC | RISC
--- | ---
Complex Instruction Set Computing | Reduced Instruction Set Computing
Single instruction can execute several low lever ops (like load from memort, arithmentic ops, memory store) | B2
multi-step operations capability | single step
VLSI Advantages | 
- Less Transistors |
- Extra Space |

![](/assets/images/2021-08-20-11-53-40.png)

### AVR RISC

Advanced Virtual RISC
8 Bit Bus,
Harvard Architecture

AVR range = 8bit to 32 bit RISC MCU
Speed = 16 to 32 MIPS (million instructions per sec) and pin counts from 8 to 100 pins
Flash memories from 1K to 256K

![](/assets/images/2021-08-20-11-58-28.png)


![](/assets/images/2021-08-20-12-07-04.png)

![](/assets/images/2021-08-20-12-08-24.png)


![](/assets/images/2021-08-20-12-14-19.png)

![](/assets/images/2021-08-20-12-18-03.png)

![](/assets/images/2021-08-20-12-18-11.png)

![](/assets/images/2021-08-20-13-14-24.png)


```
# include <avr/io.h>
int main(void)

{
    unsigned char temp;
    DDRB = 0x00;
    DDRC = 0xFF; //display I u
    while(1)
    {
        temp = PINB;
        PORTC = temp +5;

    }
    return 0;

}
```

![](/assets/images/2021-08-20-13-23-44.png)

```
# include <avr/io.h>
int main(void)

{
    unsigned char temp;
    DDRC = 0x00;
    DDRB = 0xFF;
    DDRD = 0xFF;
    while(1)
    {
        temp = PINC;
        if(temp<100)
        {
            PORTB = temp

        }
        else
        {
            PORTD = temp
        }
    }
    return 0;

}

```

![](/assets/images/2021-08-20-13-33-33.png)

### Port Registers - Portx

PORTx - Port Driver Register

![](/assets/images/2021-08-20-13-34-23.png)

![](/assets/images/2021-08-20-13-36-21.png)

Question

![](/assets/images/2021-08-20-13-40-04.png)

```
# include <avr/io.h>
int main(void)

{
    DDRB=0xFF;
    unsigned char i;
    for(i=-4;i<=4;i++)
    {
        PORTB = i;
    }
    return 0;

}
```
![](/assets/images/2021-08-20-13-47-28.png)


If Frequency = 1MHz,  
So Time Period = 1 micro second  == 10<sup>-3</sup> second


![](/assets/images/2021-08-20-14-20-17.png)

Not sure which is correct
```
#include <avr/io.h>

int main() 
{        
    // Setting port B and C to output
    DDRB = 0xFF;
    DDRC = 0xFF;
    // Initializing the input constant
    unsigned int given_bcd = 0x29;

    while(1)
    {
        unsigned int quotient = given_bcd / 16;
        unsigned int remainder = given_bcd % 16;
        PORTB = quotient;
        PORTC = remainder;
    }
    return 0;
}

```
Not Sure
```
#include <avr/io.h>

int main() 
{        
    // Setting port B and C to output
    DDRB = 0xFF;
    DDRC = 0xFF;
    // Initializing the constants
    unsigned int given_bcd = 0x29;
    unsigned int ascii_differnce = 30;

    while(1)
    {
        unsigned int quotient = given_bcd / 16;
        unsigned int remainder = given_bcd % 16;

        PORTB = quotient + ascii_differnce;
        PORTC = remainder + ascii_differnce;
    }
    return 0;
}

```