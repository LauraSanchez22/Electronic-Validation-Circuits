# **NPN transistor switching circuit**

#### Project: NPN Transistor (2N2222) Switching Circuit
#### Author: Laura Lizbeth Sanchez Ramirez
#### Software: Proteus 8 Professional

## **Electrical diagram components**

- Power supply: VCC = 5V
- Transistor: 2N222 (NPN type BJT).
- Resistors: 
  - RB = 10kΩ (base current-limiting).
  - RCO = 1KΩ (collector current limiter).
  - RLED = 220Ω (LED current-limiting).
- PINK LED:
  - Electric voltage ≈ 2V
- BJT Transistor:
  - VBE ≈ 0.7V 
  - Collector-emitter saturation voltage: 0.2V

## **Circuit analysis**

### Estimated LED current

Upon actuating the switch, a voltage of 0.19 V is observed; consequently, the pink diode 
is in a non-conducting state (normally, when actuated, its voltage is 2.2 V), which means 
that the current flowing through it upon actuation is negligible.

**ILED ≈ 0mA**

The combination of the 1kΩ and 220Ω resistor connections creates such a drastic voltage division 
that the emitter fails to deliver the voltage required to light up the pink LED.

### Anomalous operating point

The transistor is not functioning as a switch to turn on an LED; instead, it is in an incorrect bias 
region where the emitter voltage is very low, causing energy dissipation without actually turning on the pink LED.

**VCE = VC - VE = 5V -VE** 


## Results obtained

| Parameter                     | Value        | Observation                        |
| ----------------------------- | ----         | ---------------------------------  |
| VCC                           | 0.5V         | Circuit power supply.              |
| VLED                          | 0.19V        | The LED's behavior indicates a critical state: it is off because the voltage across its terminals is below the conduction threshold required to turn it on.                                    |
| Transistor collector current  | Short circuit| Optimal result.                    |
| Switch                        | Invested     | When the switch is pressed, the LED is off, but when it is not pressed, the LED remains on.    
                                                                                    |


## Simulations

The implemented methodology consists of performing functional tests on the circuit to verify the 
results for each component, checking their behavior against the electrical connections made.

![Texto alternativo]("BJT_Circuit.png")

![Texto alternativo]("BJT_Circuit_Led_ON.png")

## Modifications to the circuit (evidence)

### Pink LED current

The diode is forward-biased and limited by a 220-ohm resistor; the LED receives power but 
ignores the switch position.

**ILED = (VCC - VLED) / RLED** = (5V - 2.24V) / 220Ω = 2.76V / 220Ω = 12.54mA

### Base current

**IB = (VCC -VBE(SAT)) / RB** = (5V - 0.7) / 10KΩ = 0.43mA

### Unstable collector current

Since the collector is directly connected to VCC without any intervening resistor, the collector 
current tends to rise to a high value.


![Texto alternativo]("Modified_BJT_Circuit.png")


## Results obtained from the modified simulation

| Parameter                     | Value        | Observation                                                                                |
| ----------------------------- | -------      | -------------------------------------------------------------------------------            |
| VCC                           | 0.5V         | Circuit power supply.                                                                      |
| VLED                          | 0.24V        | Confirmation that the LED is forward-biased by the resistor, without transistor regulation.|
| ILED                          | 12.54mA      | A continuous flow of current keeps the LED on.                                             |
| IC                            | Very high    | A short circuit occurs.                                                                    | 
| LED                           | ON           | It stays on all the time; it does not respond to the switch.                               |   
                                                                                  

## Correct functional result for the circuit

When the switch is open, the transistor remains off, blocking current flow; this keeps the 
LED off and the voltmeter reading at 0.

![Texto alternativo]("NPN_Transistor_Switching_OFF.png")

When current enters the transistor's base, the transistor activates, acting as a closed circuit 
to ground; current flows from the 5V source through the 220Ω resistor, lighting up the pink LED. 
However, this results in a voltage drop of 2.23V as measured by the voltmeter.

![Texto alternativo]("NPN_Transistor_Switching_ON.png")

As part of the modifications to this final design, some connections were changed and the 1 kΩ 
resistor was removed.

## Mathematical analysis of the corrected circuit

### Base current

**Ic = (VCC - VBE(SAT)) /RB** = (5V - 0.7V) / 10KΩ = 0.43mA

### Collector current and Pink LED

**IC = (VCC - VF - VCE(SAT)) / RLED** = (5V - 2.23V - 0.2V)/ 220Ω = 2.57 / 220Ω = 11.68mA

### Transistor equilibrium operating point

IEQ = IC -IB = 11.68mA + 0.43mA = 12.11mA

**Q = (VCE(SAT), ICQ)** = (0.2V, 11.64mA) 

## Results obtained from the corrected simulation

| Parameter                     | Value  | Observation                                                           |
| ----------------------------- | ----   | -------------------------------------------------------------------   |
| VBE                           | 0.7V   | Within the expected range.                                            |
| VCE(SAT)                      | 0.2V   | Minimum voltage that allows the transistor to act as a closed switch. |
| VCC                           | 5V     | Continuous voltage for the entire circuit.                            |
| IB                            | 0.43mA | Sufficient current to ensure transistor saturation.                   |
| VF                            | 2.23V  | Voltage drop measured with a voltmeter.                               |
| IC                            | 11.68mA| Optimal current flow for safe ignition without overheating.           |
| IEQ                           | 12.11mA| Total return path for drained current directly to GND.                |
