# Side-channel attacks on high-security electronic safe locks

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Plore)

This talk focuses on Group 1 UL listed locks.  Not cheap hotel-safe locks, but not GSA-approved high security locks.  The focus is on the type of locks found on large commercial gun, burglary and fire safes.

## First Target
S&G 6120

The logic exists inside the safe, battery, buzzer and keypad outside.

![6120 system model](../talks/6120-System-Model.png)

Add a pullup resistor to the battery, monitor the voltage with an oscilliscope, and you can see the difference in voltage of a 0 vs 1 as the ECU reads the key code from the eeprom in clear text.  Decode the value from binary to decimal, punch it in on the keypad, the lock opens.

![6120 circuit model](../talks/6120-Circuit-Model.png)

## Second Target
S&G Titan PivotBolt

### How does it work?
Uses an STM8S105K6 microcontroller, internal storage, so you can't observe a voltage difference as it reads from the eeprom.

As a lesson learned though, the old lock does the comparison one digit at a time.  If there's a mismatch, it will abort and do other things, which you can observe as a drop in the power utilization of the lock.

28ms difference per correct digit before the power falls.  This allows for a far more efficient search of the keyspace for the correct keycode.  Unfortunately, it implements a penalty lockout after 5 tries, for 10 minutes, making the naive search still prohibitive.

So... can we cut power before the pentaly count is written?  He Got a copy of the microcontroller used in the lock and experimented.
If you kill power 500us to 2.5ms after the start of the write, the memory will contain not the original value, or the new value, it will contain a zero.
Fortunately, the lock firmware appears to treat zero as a value valid.  :-D  So, kill power after the write to the incorrect attempt counter.

Can you cause the voltage to drop fast enough?

Key on the current rise as it starts to compare the combination, start at a lower voltage, and cut the voltage a shade early, and it easily falls into the brownout voltage of the CPU (triggering the write of a zero to the eeprom).  Excellent!

### Automating the attack
To implement this, you really need a custom PCB to run the attack.  It needs a micro-ammeter, power supply and control for the lock, and a keypress simulator.  The attack code runs several runs of each combinat (oversampling) so that it can measure the accuracy of a given combination.  The full attack takes about 15 minutes.

## General Observations
Burglars aren't going to bother with this.  They'll use a sawzall, or a hydraulic floor jack from your garage.  But, there are some lessons which are applicable for other types of lockout systems.
* Don't store the data in the clear (eg. in the eeprom, as in the 6120).
* Do your comparison in constant time, don't abort early, comprae all the digits every time.
* Assume failure first, increment the failure counter first, then clear it if the combination was entered successfully.
* The cleared value (zero, in this case) should not be considered a valid value.
* Use a GSA-approved lock, which are specifically designed to defend against this type of attack.
