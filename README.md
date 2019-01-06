# Stellax_3.5
Slave computer(stm32f103rc) controling and communication

## Structure:
- Distance Measurement:
Configure iic and make use of KS103, return the distances in 5 direction. 

	- 24cxx.h					    24cxx.c
	- myiic.h					    myiic.c
	- ultrasonic.h  	    ultrasonic.c

- Serial Port Communicatoin:
Communicate with master computer,  which is used for data transmission, including state data, control data and order etc.

	- stellax_usart.h			stellax_usart.c
	
- Motor Control:
Control the motor according to the control data.
	
	- pwm.h pwm.c

- Speedometer:
Measure the actural speed of stellax
	
	- timer.h timer.c 
	- wheel.h wheel.c

- Introspection：
Check all of the modules, and show their state by lighting the LED. 
	
	- check.h check.c
