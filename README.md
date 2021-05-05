# SAMC21 TCC GPIO toggle counter
This demo will using TCC to count an external gpio toggle times, every falling edge of the gpio will increase the counter number of the TCC.

The function implemented by using EIC->EVSYS->TCC, the EIC using *Synchronous edge detection mode* for better filter glitch,
the GCLK_EIC should be fast enough compared to the GPIO toggle frequences, the Demo using 48Mhz for EIC, EVSYS, and TCC2.
The EVSYS must select Asynchronous mode for TCC event input according to the errata.

The application can using **TCC2_Compare16bitCounterGet()** function to get the counter value,
or using **TCC2_Compare16bitCounterSet( uint16_t count )** to reset the counter value.
More function like STOP/START_RETRIGGER can be using **TCC2_CompareCommandSet(TCC_COMMAND command)**

## Demo
The Counter register will updated after calling the **TCC2_Compare16bitCounterGet()**, the demo generated 4
falling edges by click 4 times of the SW0 button of the ATSAMC21-XPRO EVB.
![image](https://user-images.githubusercontent.com/20182981/117145341-a3abe680-ade5-11eb-906e-a76f266ee1b6.png)
