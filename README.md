# Watchdog-timern för ATmega328P i C.
Implementering av drivrutiner för Watchdog-timern, som möjliggör systemåterställning eller
avbrottsgenerering ifall ett givet program fastnar i en loop eller dylikt.

Filen "ATmega328P device drivers C - WDT demo start_code.zip" innehåller startkod för projektet,
vilket innefattar diverse drivrutiner för mikrodator ATmega328P, funktionsbeskrivningar för
drivrutinerna som ska implementeras för Watchdog-timern samt instruktioner för vad som ska läggas 
till för att testa drivrutinerna (i main.c samt isr.c).

Resterande filer utgör samma projekt med färdigskrivna drivrutiner för Watchdog-timern.
Watchdog reset genereras via nedtryckning av en tryckknapp ansluten till pin 13 (PORTB5).
I programmet aktiveras Watchdog-timern i Interrupt Mode med en timeout på 8192 ms. 
Om Watchdog-timern inte återställs var åttonde sekund genereras därmed ett Watchdog-avbrott
(avbrottsvektor WDT_vect). 

Efter fem Watchdog-avbrott låses programmet och en lysdiod ansluten till pin 8 (PORTB0) 
blinkar var 50:e ms (via timerkrets Timer 1). Det enda sättet att låsa upp programmet och
stoppa blinkningen är att genomföra en systemåterställning, exempelvis via reset-knappen.
Meddelanden om antalet passerade Watchdog-timeouts, Watchdog reset samt systemlåsning 
skrivs ut i ansluten seriell terminal via USART.

Se video tutorial här:
https://youtu.be/nlO3Z-1vmCs