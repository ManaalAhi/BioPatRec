# GUI\_TestPWMs #

This GUI was created to test the pulse width modulation (PWM) with the [ALC](ALC.md).

The GUI consists of 2 main parts:

## Initialize the serial connection ##
> There are 2 buttons (''Connect, Disconnect'') which handles the communication
  * Connect: Calls "Connect\_ALC" which returns the communication object saved in the  handles as "com". The "com" object is necessary for all future   communication.
  * Disconnect:  Close the 'com' object.


## Control ##

  * Update PWMs: Calls ''UpdateAllPWMusingSCI'' to update all PWMs using and ID per each PWM (A,B,C,...,L). The function returns a 1 or 0 depending if it was successful or not. It starts by sending a 'S', then a 'A','B',...,'L' as the PWMs IDs. See [Motors\_Protocol](Motors_Protocol.md)

> NOTE: The value of duty cycle will remain until it is over-written by another function so '''be careful''' if the hand is connected.

  * Cycle PWM: Calls 'TestPWMusingSCIbyCycling' and first sends a 'T', then a 'B' as the function ID. Then a loop is called that decreases the pwm duty cycle with every run. Each PWM is updated to the current speed of the loop while the second, related PWM is held low. There is a moving forward and barwards cycle. No IDs per PWM is used here.

> NOTE: The duration of the cycles might bring the motors to the ends SO becareful if the hand is connected.

> The update and cycle routines are two different ways to communicate with the ALC and control the PWMs.

> NOTE: As any other testing routine for the ALC, there is a corresponding routine in C in ALC. The routines used here are in the PWMs.c file.


The name of the matlab function and C function in the [ALC](ALC.md) must match each other in order to ease the identification.


