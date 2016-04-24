# gasGauge

The gasGauge program is an Arduino-based microcontroller program used to compensate replacement fuel tank sending units that use a linear scale. In this particular case, it was used for a 1984 Dodge Ram Charger with ~35 gallon tank. However, the formula used to calculate the entire range should be fairly accurate for all 73-10 ohm fuel sending units. That being said, because the original gauges were analog, and each had/have their own "finesse points," this algorithm has been precision tweaked for the vehicle in question.

#History

The original sending unit and gas gauge of most pre-1986 Ford's and Chrysler vehicles worked on a logarithmic scale which provided "weight" to both the full and empty side of the tank. However, because the original parts are no longer made, and the only replacement parts (that we know of) use linear sending units rather than logarithmic ones, most gas gauges on vehicles using this type of sending unit are ridiculously inaccurate.

In order to fix this problem, GasGauge was created to serve as a microprocessor based tool placed between the fuel tank sending unit and the analog instrument gauge. It should be noted that some electrical work is also required in order to make this work properly.

#Hardware Configuration

In order for this to work correctly, several modifications to the vehicle's electrical system will be required. For most people, this is generally a game changer, but it need not be. 
  1. See the schematic labeled gasGaugeCircuit in the top level of this repository on how to make changes to the fuel sensing circuit. It may be possible to deviate from the part numbers/values listed in the schematic, but the ones listed have been proven to work for our particular scenario.
  2. This ONLY works with 5V fuel systems. 12V and 6V systems will NOT run without further modification and code refactoring.


#How to Compile
Because gasGauge was designed using an Arduino, it should be important to note a few things: 
  1. The original design was used with an Arduino Uno. However, any Arduino with an ATMEL 328 chip and a 5V analog output should work. That being said, it would be impractical to account for every single pin orientation of all the Arduino units. The analog input pin is set to a0 and the PWM output pin to pin 11. Pay close attention to the input and output pins on your Arduino to ensure they exist and/or are correct!  
  2. Connect the Arduino to your computer. Open a new Arduino sketch and paste the gasGauge code (see file named "gasGauge.ico" at the top-level of this repository.
  3. If you want to look at the inputs and outputs going to the Arduino, you can open a serial monitor window. It will show you 

