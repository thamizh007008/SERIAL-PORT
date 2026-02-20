
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
#include <reg51.h>

void main(void)
{
    TMOD = 0x20;      // Timer1 Mode2
    TH1  = 0xFD;      // 9600 baud rate
    SCON = 0x50;      // Serial mode1
    TR1  = 1;         // Start Timer1

    SBUF = 'A';       // Send character 'A'
    while(TI == 0);   // Wait until transmitted
    TI = 0;           // Clear flag

    while(1);         // Stop here
}



```
### (ii) Serial Port to Transfer a Message

```
#include <reg51.h>

void main(void)
{
    unsigned char msg[] = "VETRI";
    unsigned char i;

    TMOD = 0x20;      // Timer1 Mode2
    TH1  = 0xFD;      // 9600 baud rate
    SCON = 0x50;      // Serial mode1
    TR1  = 1;         // Start Timer1

    for(i = 0; msg[i] != '\0'; i++)
    {
        SBUF = msg[i];
        while(TI == 0);
        TI = 0;
    }

    while(1);
}




```

### OUTPUT:
<img width="1907" height="993" alt="image" src="https://github.com/user-attachments/assets/6ab022ed-dd68-4a38-9488-aafade0e410d" />

<img width="1919" height="1013" alt="image" src="https://github.com/user-attachments/assets/0eaa7d03-5232-4d33-9ebf-2fd6528aaf3d" />



### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
