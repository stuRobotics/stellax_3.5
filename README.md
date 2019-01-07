# Stellax_3.5
Slave computer(stm32f103rc) controling and communication

## Program Structure:
<img src=https://github.com/stuRobotics/stellax_3.5_stm32/blob/master/img/Structure.svg width=500/> <br>  
- **Distance Measurement**:<br>  
Configure iic and make use of KS103, return the distances in 5 direction.<br>  
	- 24cxx.h					    24cxx.c
	- myiic.h					    myiic.c
	- ultrasonic.h  	    ultrasonic.c 
	
- **Serial Port Communicatoin**:<br>  
Communicate with master computer,  which is used for data transmission, including state data, control data and order etc.<br>  
	- stellax_usart.h			stellax_usart.c
	
- **Motor Control**:<br>  
Set the speed of the motor according to the control data.<br>  
	- pwm.h pwm.c
	
- **Speedometer**:<br>  
Measure the actural speed of stellax.<br>  
	- timer.h timer.c 
	- wheel.h wheel.c
	
- **Introspection**:<br>  
Check all of the modules, and show their state by lighting the LED. <br>  
	- check.h check.c

## Types of Data:
- **Speed**:<br>
<img src=https://github.com/stuRobotics/stellax_3.5_stm32/blob/master/img/Speed.png width=300 /> <br>  
```C
typedef union
{
	short int f;
	unsigned char c[2];
}Speed;
```
- **Distance**: <br>
<img src=https://github.com/stuRobotics/stellax_3.5_stm32/blob/master/img/Distance.png width=300/> <br> 
```C
typedef union
{
	u16 d;
	unsigned char c[2];
}Distance;
```
- **State data**: <br> 
The state data is sent to the master computer by serial port, which contain the actural speed of two wheels and the obstacle distance in 5 directions. 's' indicates the beginning of data, 'e' indicates the end of data. <br> 
<img src=https://github.com/stuRobotics/stellax_3.5_stm32/blob/master/img/state_data.png /> <br>  

- **Control data**: <br>
The control data is received from the master computer by serial port, which contain the expected speed of two wheels. <br> 
<img src=https://github.com/stuRobotics/stellax_3.5_stm32/blob/master/img/Control_data.png width=400/> <br>  
