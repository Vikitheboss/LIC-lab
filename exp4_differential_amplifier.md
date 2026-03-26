# EXPERIMENT 4  
## Differential Amplifier – DC, Transient and AC Analysis

---

## INTRODUCTION

A differential amplifier is one of the most fundamental building blocks in analog electronics and integrated circuit design. It is designed to amplify the difference between two input signals while rejecting signals that are common to both inputs. This makes it highly effective in reducing noise and interference in electronic systems.

The basic structure of a differential amplifier consists of two matched transistors connected to a common current source, known as the tail current source. The input signals are applied to the gates of the transistors, and the output is taken from the drain terminals. When identical signals are applied to both inputs, the output ideally becomes zero, demonstrating perfect common-mode rejection.

Differential amplifiers are widely used in operational amplators, instrumentation systems, and communication circuits due to their high accuracy and noise rejection capability. In this experiment, a MOSFET-based differential amplifier is analyzed using simulation tools to study its DC, transient, and AC characteristics.

---

## THEORY

A differential amplifier amplifies the difference between two input voltages while suppressing any common signal present at both inputs. The circuit consists of two identical MOSFETs sharing a constant current source. The current is divided between the two transistors depending on the input voltages.

When both inputs are equal, the current is equally distributed, resulting in zero output difference. When there is a difference between the inputs, the current shifts, producing a differential output.

### Differential Gain (A_d)

The differential gain is given by:

A_d = g_m × R_D

where  
g_m = 2I_D / V_ov  

g_m is the transconductance,  
I_D is the drain current,  
V_ov is the overdrive voltage,  
R_D is the drain resistance.

---

### Common Mode Gain (A_cm)

The common mode gain represents amplification of signals that are common to both inputs. Ideally, this value is zero, but practically it is small.

---

### Common Mode Rejection Ratio (CMRR)

CMRR indicates how effectively the amplifier rejects common-mode signals:

CMRR = A_d / A_cm

A higher CMRR means better noise rejection.

---

### Input Common Mode Voltage (V_CM)

The input common-mode voltage is defined as:

V_CM = (V_1 + V_2) / 2

---

### Minimum Common Mode Voltage (V_CM(min))

The minimum value of V_CM is determined by the condition that the tail current source and input transistors remain in saturation:

V_CM(min) = V_T + V_ov + V_DS(sat, tail)

---

### Maximum Common Mode Voltage (V_CM(max))

The maximum value of V_CM is limited by the requirement that the transistors remain in saturation:

V_CM(max) = V_DD − V_ov − V_DS(sat)

---

### Operating Condition

For proper operation:

V_CM(min) ≤ V_CM ≤ V_CM(max)




## GIVEN DESIGN PARAMETERS

- Channel Length (L) = 480 nm  
- Power (P) ≤ 1.8 mW  

---

## SUPPLY AND INPUT CONDITIONS

- VDD = 0.9 V  
- VSS = -0.9 V  
- VinCM = 0 V  
- Vocm = 0 V  
- Vp = -0.7 V  

---

## ADDITIONAL PARAMETER

- Load Capacitance (CL) = 10 pF  

---
## CIRCUIT DIAGRAM
<img width="1226" height="722" alt="image" src="https://github.com/user-attachments/assets/29a55b59-4743-4bc6-ba78-4a5d19f5edab" />




# DC ANALYSIS (OPERATING POINT)

<img width="885" height="616" alt="image" src="https://github.com/user-attachments/assets/cb702078-94ce-49be-93dd-434e991338d7" />


---

## NODE VOLTAGES

| Node      | Voltage (V)        |
|----------|-------------------|
| V(n001)  | 0.9               |
| V(n002)  | 0                 |
| V(n003)  | 0                 |
| V(n004)  | -0.9              |
| V(vout1) | 3.90313e-16 ≈ 0   |
| V(vout2) | 0                 |
| V(vs)    | -0.707107         |

---

## SOURCE CURRENTS

| Source | Current (A) |
|--------|------------|
| I(V1)  | 0          |
| I(V2)  | 0          |
| I(V3)  | 0.001      |
| I(V4)  | -0.001     |

---

## RESISTOR CURRENTS

| Resistor | Current (A) |
|----------|------------|
| I(R1)    | 0.0005     |
| I(R2)    | 0.0005     |

---

## MOSFET M1 PARAMETERS

| Parameter | Value (A)        |
|----------|----------------|
| Id(M1)   | 0.0005         |
| Ig(M1)   | 0              |
| Ib(M1)   | -7.17107e-13   |
| Is(M1)   | -0.0005        |

---

## MOSFET M2 PARAMETERS

| Parameter | Value (A)        |
|----------|----------------|
| Id(M2)   | 0.0005         |
| Ig(M2)   | 0              |
| Ib(M2)   | -7.17107e-13   |
| Is(M2)   | 0.0005         |

---

## OBSERVATIONS

- Output voltage ≈ 0 → Balanced differential condition  
- Id(M1) = Id(M2) → Proper symmetry  
- Negligible gate and bulk currents  
- Equal resistor currents → Correct biasing  

---

## CONCLUSION

The circuit operates correctly in DC with proper biasing and symmetry, confirming expected differential amplifier behavior.







## Common Mode Input Range Calculation

### Given:
- VDD = 0.9 V  
- VSS = -0.9 V  
- VP = -0.7 V  
- Vout,CM = 0 V ⇒ VD = 0 V  
- VT = 0.366 V  

---

## 1. Calculation of VCM(min)

### Condition:
For NMOS to just turn ON:
VGS = VT  

### Formula:
VCM(min) = VP + VT  

### Substitution:
VCM(min) = -0.7 + 0.366  

### Result:
VCM(min) = -0.334 V  

---

## 2. Calculation of VCM(max)

### Condition:
For NMOS to remain in saturation:
VDS = VOV  

---

### Step 1: Drain-Source Voltage
VDS = VD - VS  
VDS = 0 - (-0.7)  
VDS = 0.7 V  

---

### Step 2: Overdrive Voltage
VOV = VGS - VT  

VGS = VCM - VP  
VGS = VCM + 0.7  

So,
VOV = (VCM + 0.7) - 0.366  
VOV = VCM + 0.334  

---

### Step 3: Apply Saturation Condition
VDS = VOV  

0.7 = VCM + 0.334  

---

### Step 4: Solve
VCM = 0.366 V  

---

## Final Results:

VCM(min) = -0.334 V  
VCM(max) = 0.366 V  

---

## Conclusion:

The common-mode input voltage range is:

-0.334 V ≤ VCM ≤ 0.366 V  

The lower limit ensures transistor turn-on, and the upper limit ensures saturation operation.






## Common Mode Voltage Limits (VCM min and VCM max)

---
<img width="1441" height="675" alt="image" src="https://github.com/user-attachments/assets/ef218bc8-abab-4cc1-aed9-b41cdae40644" />

## Introduction

The common-mode input voltage is defined as:

VCM = (Vin1 + Vin2) / 2

For proper operation of a MOS differential amplifier, both transistors must remain in saturation region. This gives two limits:
- VCM(min)
- VCM(max)

---

## Condition for Saturation

For NMOS:

VDS ≥ VGS - VT

---

## VCM(min) Derivation

At minimum common-mode voltage, transistor is just ON:

VGS = VT

We know:

VGS = VG - VS

So,

VT = VCM(min) - VS

Rearranging:

VCM(min) = VS + VT

---

### Using simulation values:

VS = -0.707 V  
VT = 0.366 V  

VCM(min) = -0.707 + 0.366  
VCM(min) ≈ -0.34 V

---

## Result

VCM(min) ≈ -0.34 V

---

## Observation

At this point:
- VGS ≈ VT  
- Overdrive voltage ≈ 0  
- Transistor is just turned ON  

---

## VCM(max) Derivation

At maximum common-mode voltage, transistor leaves saturation:

VDS = VGS - VT

We know:

VD - VS = VGS - VT  
VD - VS = (VCM(max) - VS) - VT  

Simplifying:

VD = VCM(max) - VT  

So,

VCM(max) = VD + VT

---

### Using simulation values:

VD = 0 V  
VT = 0.366 V  

VCM(max) = 0 + 0.366  
VCM(max) ≈ 0.366 V

---

## Result

VCM(max) ≈ 0.366 V

---

## Final Summary

VCM(min) = -0.34 V  
VCM(max) = 0.366 V  

---

## Conclusion

The differential amplifier operates correctly in the range:

-0.34 V ≤ VCM ≤ 0.366 V

Below VCM(min): transistor goes to cutoff  


---

## Key Point

VCM(min) → determined by turn-on condition  


## Transient Analysis at VCM(min)
<img width="1919" height="509" alt="image" src="https://github.com/user-attachments/assets/aacf6c30-2850-4cdc-a076-b9a5f86928bb" />

At VCM(min), the input signal is applied as a sine wave.

However, the output remains constant (no variation observed).

This is because:

VGS ≈ VT  
Overdrive voltage (Vov) ≈ 0  

Due to this, the transconductance (gm) is nearly zero, and the transistor is just at the edge of conduction.

Hence, no amplification occurs and output remains flat.

---

## Conclusion

At VCM(min), the differential amplifier does not amplify the signal and acts as a non-functional amplifier.






## Operating Point at VCM(max)
<img width="1385" height="624" alt="image" src="https://github.com/user-attachments/assets/4b97c461-5985-4695-9e6b-f56c8f39a16f" />

From simulation:

VG = 0.366 V  
VS = -0.707 V  
VD = 0 V  

---

### Calculation

VGS = VG - VS  
VGS = 0.366 - (-0.707) = 1.073 V  

Vov = VGS - VT  
Vov = 1.073 - 0.366 = 0.707 V  

VDS = VD - VS  
VDS = 0 - (-0.707) = 0.707 V  

---

### Condition

VDS = Vov  

---

## Conclusion

At VCM(max), the MOSFET operates at the boundary between saturation 

Any further increase in VCM will push the transistor into triode region, resulting in distortion and loss of amplification.



## Transient Analysis at VCM(max)
<img width="1918" height="507" alt="image" src="https://github.com/user-attachments/assets/bc76eca8-2b14-430d-a8ca-930aa60ea706" />


At VCM(max), a sinusoidal input signal is applied.

However, the output remains nearly constant (no amplification observed).

This is because:

VDS = Vov  

The MOSFET operates at the boundary of saturation and enters triode region for small signal variations.

Due to this, transconductance decreases and the amplifier loses its gain.

---

## Conclusion

At VCM(max), the differential amplifier fails to amplify the input signal and becomes non-functional.




# TRANSIENT ANALYSIS (VID < √2 VOV CONDITION)

## OUTPUT WAVEFORM

![Linear Output Waveform]
<img width="1888" height="411" alt="image" src="https://github.com/user-attachments/assets/b7d7f7ac-71e4-46e5-b1ff-b90a99bbea4a" />


---

## GRAPH DETAILS

| Parameter            | Value / Description        |
|---------------------|--------------------------|
| Condition           | \( V_{id} < \sqrt{2}V_{OV} \) |
| Output Observed     | V(vout1), V(vout2)       |
| Waveform Type       | Sinusoidal               |
| Amplitude Scale     | nV (very small)          |
| Nature              | Linear                   |

---

## OBSERVATIONS

- The output waveform is **smooth and sinusoidal**  
- No distortion or clipping is observed  
- Both transistors are operating in **saturation region**  
- The circuit behaves as a **linear amplifier**  

---

## ANALYSIS

For differential amplifier:

\[
V_{id} = V_1 - V_2
\]

Condition for linear operation:

\[
V_{id} < \sqrt{2}V_{OV}
\]

Since this condition is satisfied:
- Both MOSFETs conduct simultaneously  
- Current is shared between them  
- Output remains **linear**

---

## IMPORTANT NOTE

- The output amplitude is very small (**in nV range**)  
- This is because:
  - Single-ended output is observed  
  - Input signal is very small  

For better observation:
- Plot differential output:
  \[
  V_{out} = V(vout1) - V(vout2)
  \]

---

## CONCLUSION

The condition \( V_{id} < \sqrt{2}V_{OV} \) ensures linear operation of the differential amplifier. The obtained sinusoidal waveform confirms that the circuit is operating in the linear region, although the output amplitude is small.




# TRANSIENT ANALYSIS (VID > √2 VOV)

## OUTPUT WAVEFORM

![Non-linear waveform]
<img width="1906" height="383" alt="image" src="https://github.com/user-attachments/assets/40c0aaf9-d71a-43b5-bfdd-61aebe148a23" />


---

## OBSERVATIONS

- The output waveform is **distorted and non-sinusoidal**  
- A DC offset is present in the signal  
- The waveform shows **asymmetry and sharp peaks**  
- Output amplitude is reduced  

---

## ANALYSIS

When:
\[
V_{id} > \sqrt{2}V_{OV}
\]

- One MOSFET enters **cutoff region**  
- The other MOSFET carries the **entire tail current**  
- Current is not equally shared  

This leads to:
- Non-linear operation  
- Distorted output waveform  

---



# COMPARE AND INTERPRET THE ANALYSIS

## COMPARISON OF RESULTS

| Parameter / Condition        | \( V_{id} < \sqrt{2}V_{OV} \) | \( V_{id} > \sqrt{2}V_{OV} \) |
|-----------------------------|------------------------------|------------------------------|
| MOSFET Operation            | Both in saturation           | One in cutoff, one active    |
| Current Distribution        | Equal sharing                | Unequal (one dominates)      |
| Output Waveform             | Sinusoidal                   | Distorted / non-linear       |
| Linearity                   | Linear region               | Non-linear region            |
| Gain Behavior               | Constant                    | Varies (non-linear gain)     |
| Symmetry                    | Symmetrical                 | Asymmetrical                 |
| Signal Quality              | High (clean output)         | Poor (clipping/distortion)   |

---

## INTERPRETATION

A differential amplifier amplifies the **difference between two input signals** while rejecting common components :contentReference[oaicite:0]{index=0}. The behavior of the circuit strongly depends on the magnitude of the differential input voltage.

### 🔹 Case 1: \( V_{id} < \sqrt{2}V_{OV} \)

- Both MOSFETs remain in **saturation region**  
- Tail current is **shared equally**  
- Output is **linear and sinusoidal**  
- Amplifier behaves as an **ideal differential amplifier**  

👉 This is the **desired operating region**

---

### 🔹 Case 2: \( V_{id} > \sqrt{2}V_{OV} \)

- One MOSFET enters **cutoff region**  
- Other MOSFET carries **entire current**  
- Circuit loses symmetry  
- Output becomes **distorted and non-linear**  

This is **undesired region**

---

## PHYSICAL MEANING

- Differential pair works by **steering current between two transistors**
- For small inputs:
  - Current splits smoothly → **linear output**
- For large inputs:
  - Current fully shifts to one side → **switch-like behavior**

---

## FINAL CONCLUSION

- The condition \( V_{id} < \sqrt{2}V_{OV} \) ensures **linear amplification**
- Exceeding this limit causes **cutoff and distortion**
- Hence, proper input selection is essential for **accurate differential amplifier operation**

---


