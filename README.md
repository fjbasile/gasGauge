# gasGauge

The gasGauge program is an Arduino-based microcontroller program used to compensate replacement fuel tank sending units that use a linear 73-10 ohm scale. In this particular case, it was used for a 1984 Dodge Ram Charger with an ~35 gallon tank. However, the formula used to calculate the entire range should be fairly accurate for all 73-10 ohm fuel sending units. That being said, because the original gauges were analog, and each had/have their own "finesse points," this algorithm has been precision tweaked for the vehicle in question. As such, there may be small differences between vehicles in terms of exact empty, exact full, and half tank. Nonetheless, these differences should be nothing dramatic, and may not even be noticeable. Because of that, experimentation is recommended, but not necessarily required. Furthermore, any changes made should be to the programming code - not the external circuitry.

#History

The original sending unit and gas gauge of most pre-1986 Ford's and Chrysler vehicles worked on a logarithmic scale which provided "weight" to both the full and empty side of the tank. However, because the original parts are no longer made, and the only replacement parts (that we know of) use linear sending units rather than logarithmic ones, most gas gauges on vehicles using this type of sending unit are ridiculously inaccurate. While some aftermarket manufacturers will sell a new gas gauge they've "calibrated" to their proprietary sending unit, this program is meant to work with existing OEM equipment.

In order to fix this problem, GasGauge was created to serve as a microprocessor based tool placed between the fuel tank sending unit and the analog instrument gauge. It should be noted that some electrical work is also required in order to make this work properly.

#Hardware Configuration

In order for this to work correctly, several modifications to the vehicle's electrical system will be required. For many, this may be a game changer, but it's truly not that complex. 
  1. See the schematic labeled "gasGauge.pdf" in the top level of this repository on how to make changes to the fuel sensing circuit. It may be possible to deviate from the part numbers/values listed in the schematic, but the ones listed have been proven to work for our particular scenario, and with this code.
  2. This ONLY works with 5V fuel systems. 12V and 6V systems will NOT run without further modification and code refactoring.


#How to Compile and Run
Because gasGauge was designed using an Arduino, it should be important to note a few things: 
  1. The original design was used with an Arduino Uno. However, any Arduino with an ATMEL 328 chip and a 5V analog output should work. That being said, it would be impractical to account for every single pin orientation of all the Arduino units. The current code sets the analog input pin to a0 and the PWM output to pin 11. Pay close attention to the input and output pins on your Arduino to ensure they exist and/or are correct!  
  2. Connect the Arduino to your computer. Open a new Arduino sketch and paste the gasGauge code (see file named "gasGauge.ico" at the top-level of this repository.
  3. Upload the sketch to your Arduino board.
  4. If you want to look at the inputs and outputs of the Arduino, you can open a serial monitor window with the Arduino in-circuit and connected to your computer.

#How It Works
The Arduino sends a 5 volt reference signal across a voltage divider. The first resistor in the voltage divider circuit is the fuel sending unit. The second resistor is of a known value close to the same range of the operating values of the sending unit. As the sending unit resistance changes (linearly) the amount of voltage returned to the Arduino also changes. The amount of voltage returned corresponds to a precise resistance value. In this way, the Arduino can accurately determine the resistance of the fuel sending unit. 

Once the resistance value is measured, it is then inserted into a quadratic equation that will correctly correspond to an output voltage. That output voltage is then converted to a PWM output signal and output on Pin 11 to the base of a PNP transistor. The PNP transistor acts as a high-level switch and allows the voltage applied to the base of the transistor to accurately and safely control the corresponding voltage to the fuel gauge. 


