# gasGauge

The GasGauge program is an Arduino-based microcontroller program used to compensate replacement fuel tank sending units that use a linear scale. In this particular case, it was used for a 1984 Dodge Ram Charger with ~35 gallon tank. The original sending unit and gas gauge are logarithmic. However, because the original parts are no longer made, and the only replacement parts use linear sending units rather than logarithmic ones, the gas gauges on these vehicles are notoriously incorrect. 

In order to fix this problem, GasGauge was created to serve as a go-between between the fuel tank sending unit and the analog instrument gauge. It should be noted that somewhat significant electrical work is also required in order to make this work properly, and that this readme only covers the software portion.

