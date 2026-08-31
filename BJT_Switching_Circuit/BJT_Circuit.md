# **NPN transistor switching circuit**

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
  - Revenue: β = 100
  - Collector-emitter saturation voltage: 0.3V

## **Circuit analysis**

### Base current

**IB= (VCC - VBE) / RB** = (5 - 0.7) /10K = 0.43mA

### Collector current

**IC = β * IB** = 100 * 0.43mA = 43mA

### Collector current measured from LED-PINK to RLED
 
**ILED = (VCC - VLED)/ RLED** = (5 - 2) /220Ω = 13.63mA

### Transistor equilibrium operating point

**IEQ = IC +IB** = 13.6mA + 0.43mA = 14.03mA

## Results obtained

| Parameter                     | Value  | Observation                        |
| ----------------------------- | ----   | ---------------------------------  |
| VBE                           | 0.7V   | Within the expected range          |
| VCE(SAT)                      | 0.3V   | Adequate saturation                |
| Base current                  | 0.43mA | Suitable value for the circuit     |
| LED current                   | 13.63mA| Optimal result                     |
| Collector current             | 43mA   | Suitable value for the circuit     |
| Equilibrium operating point   | 14.03mA| Transistor operating in saturation |

