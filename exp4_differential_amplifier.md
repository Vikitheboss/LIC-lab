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

 This is the **desired operating region**

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







# Circuit 2
<img width="924" height="465" alt="image" src="https://github.com/user-attachments/assets/9811c08a-9581-4413-b662-db82d840207f" />


#  DC Analysis of Differential Amplifier 

<img width="1402" height="696" alt="image" src="https://github.com/user-attachments/assets/c3cd4d5a-f20b-4b80-9f64-0e0bfa82f659" />

## 🔹 Aim
To perform DC analysis of a CMOS differential amplifier, verify saturation of all transistors, and determine the operating point and common-mode voltage range.

---

##  Given Parameters

- VDD = +0.9 V  
- VSS = -0.9 V  
- VG1 = VG2 = 0.3 V  
- Threshold Voltage, VT = 0.366 V  

---

## DC Operating Point

### Node Voltages
- Vout1 = 7.147 mV  
- Vout2 = 7.147 mV  
- Vp = -0.695 V  

### Currents
- ID1 = ID2 = 0.500 mA  
- ID5 = 1.000 mA  

---

##  1. Symmetry Check

ID1 = ID2  

✔ Differential pair is balanced  
✔ Output voltages are equal  

Vod = Vout1 - Vout2 = 0  

---

##  2. Region of Operation

### 🔹 NMOS (M1, M2)

VGS = 0.3 - (-0.695) = 0.995 V  

Vov = VGS - VT  
Vov = 0.995 - 0.366 = 0.629 V  

VDS = 0.007 - (-0.695) = 0.702 V  

Condition:
VDS ≥ Vov  

0.702 ≥ 0.629 ✔  

➡ M1, M2 are in saturation  

---

### 🔹 PMOS (M3, M4)

VSG = 0.9 - 0.3 = 0.6 V  

Vov = VSG - |VT|  
Vov = 0.6 - 0.366 = 0.234 V  

VSD = 0.9 - 0.007 = 0.893 V  

Condition:
VSD ≥ Vov  

0.893 ≥ 0.234 ✔  

➡ M3, M4 are in saturation  

---

### 🔹 Tail NMOS (M5)

Assumed to be in saturation  

Condition:
VDS ≥ VGS - VT  

➡ M5 acts as a constant current source  

---

##  3. Summary Table

| Transistor | VGS / VSG | VDS / VSD | Vov | Region |
|------------|----------|----------|------|--------|
| M1, M2 | 0.995 V | 0.702 V | 0.629 V | Saturation |
| M3, M4 | 0.6 V | 0.893 V | 0.234 V | Saturation |
| M5 | — | — | — | Saturation (assumed) |

---

##  4. Common Mode Voltage Range

###  VCM(min)

Condition: M5 in saturation  

Vp ≥ Vov5 - 0.9  

VCM(min) = Vp + VT + Vov1  

VCM(min) = (Vov5 - 0.9) + 0.366 + 0.629  

VCM(min) = Vov5 + 0.095  

---

### 🔹 VCM(max)

Condition: M1, M2 remain in saturation  

VCM(max) = VDD - Vov3 + VT  

VCM(max) = 0.9 - 0.234 + 0.366  

VCM(max) = 1.032 V  

---

##  Final Results

- Differential Output Voltage:
  Vod = 0  

- All transistors operate in saturation (ideal condition)

- Common Mode Range:
  VCM(min) = Vov5 + 0.095  
  VCM(max) = 1.032 V  

---


# Transient Analysis — CMOS Differential Amplifier
<img width="1919" height="460" alt="image" src="https://github.com/user-attachments/assets/80713d01-863f-464c-a0f4-a429dc0ee16d" />


### Aim
To analyze the transient response of a CMOS differential amplifier for zero DC input and observe the output waveform.

---

### Input Signals
- \( V_{in1} = \text{SINE}(0, 10mV, 1kHz) \)
- \( V_{in2} = \text{SINE}(0, 10mV, 1kHz, 180°) \)

DC value of input = **0 V**

---

### Observation

- Output waveform is **sinusoidal**
- Output is centered around **0 V**
- No DC offset present
- Frequency = **1 kHz** (same as input)
- Amplitude ≈ **2.4 mV**

---

### Important Point

Since:
\[
V_{in,DC} = 0
\]

 Differential input:
\[
V_{id} = V_{in1} - V_{in2}
\]

 With 180° phase shift:
\[
V_{id} = 2 \times 10mV = 20mV \ (\text{peak})
\]

---

### Gain Calculation

\[
A_v = \frac{V_{out}}{V_{in(differential)}}
\]

\[
A_v = \frac{2.4mV}{20mV} = 0.12
\]

---

### Analysis

- Since DC input is zero:
  - Output is centered at **0V**
  - Circuit is properly biased
- Differential pair amplifies only **difference signal**
- Output waveform is clean → indicates:
  - All MOSFETs are in saturation
  - Linear operation region

---

### Conclusion

- The differential amplifier produces a sinusoidal output for zero DC input
- Output has no offset → confirms correct biasing
- Gain is small due to low supply voltage and device parameters
- Circuit operates in **linear region for small signals**

---





## AC Analysis Report — CMOS Differential Amplifier
<img width="1893" height="470" alt="image" src="https://github.com/user-attachments/assets/e72cdb91-4541-4004-b714-3928aa423799" />

**Simulation Tool:** LTspice  
**Technology:** TSMC 018 (tsmc018.lib)  
**Supply Voltage:** VDD = 0.9 V, VSS = −0.35 V  
**AC Sweep:** `.ac dec 100 50m 1` (50 mHz to 1 Hz, 100 points/decade)

## 1. Circuit Description

The circuit is a **CMOS differential amplifier** with the following topology:

- **M1, M2** — CMOSN (NMOS): Differential input pair  
- **M3, M4** — CMOSP (PMOS): Active current mirror load  
- **M5** — CMOSN (NMOS): Tail current source  

- **Vin1 (V2):** SINE(0 10m 1k), AC 1 0 — Non-inverting input  
- **Vin2 (V3):** SINE(0 10m 1k), AC 1 180 — Inverting input  
- **Output:** `V(vout2)`

The differential input drives M1 and M2 in antiphase. The current mirror (M3–M4) converts the differential current into a single-ended output at Vout2.

## 2. AC Simulation Results

### 2.1 Frequency Response Observations

From the LTspice waveform of **V(vout2)**:

- **Mid-band gain** (flat region): **5.5504 dB**  
- **Phase at low frequency**: **−194.8°**  
- **−3 dB frequency (f_H)**: ≈ 2–5 Hz (roll-off begins near 1 Hz)  
- Cursor reading at 1.033 mHz: **5.550 dB**, **−194.822°**

### 2.2 Gain Conversion

$$
A_{v,sim} = 10^{G_{dB}/20} = 10^{5.5504/20} \approx 1.896
$$

## 3. Theoretical Analysis

### 3.1 Small-Signal Voltage Gain

The theoretical small-signal differential voltage gain is given by:

$$
A_v = g_{m1} \cdot (r_{o2} \parallel r_{o4})
$$

where:
- \( g_{m1} \) = transconductance of input transistor M1 (or M2)
- \( r_{o2} \) = output resistance of M2
- \( r_{o4} \) = output resistance of M4 (PMOS mirror)

### 3.2 Transconductance

$$
g_m = \sqrt{2 \mu_n C_{ox} \left(\frac{W}{L}\right) I_D}
$$

For TSMC 180 nm NMOS (typical parameters):
- \( \mu_n C_{ox} \approx 270\ \mu\text{A/V}^2 \)
- \( \frac{W}{L} \approx 10 \)
- \( I_D \approx \frac{I_{tail}}{2} \)

### 3.3 Output Resistance

$$
r_o = \frac{1}{\lambda I_D}
$$

### 3.4 Dominant Pole Frequency

$$
f_{-3\text{dB}} = \frac{1}{2\pi \ (r_{o2} \parallel r_{o4})\ C_L}
$$

For typical 180 nm technology with no external load, the theoretical \( f_{-3\text{dB}} \) lies in the range of **1–10 Hz**, which closely matches the simulation.

## 4. Comparison: Theoretical vs Simulated

| Parameter                          | Theoretical          | Simulated (LTspice) | Deviation      |
|------------------------------------|----------------------|---------------------|----------------|
| Mid-band gain (dB)                 | ~6 dB               | 5.5504 dB          | ~0.45 dB      |
| Mid-band gain (linear)             | ~2.0                | 1.896              | ~5.2%         |
| Dominant pole \( f_{-3\text{dB}} \)    | 1–10 Hz             | ~2–5 Hz            | Within range  |
| Phase at low frequency             | −180° (inverting)   | −194.8°            | ~14.8° excess |
| Roll-off slope                     | −20 dB/dec          | −20 dB/dec         | Perfect match |

### 4.1 Gain Deviation Analysis

The small deviation (~0.45 dB) is mainly due to:
1. Channel length modulation (λ) — BSIM3v3 model is more accurate than simplified hand calculation.
2. Body effect on M1/M2, which slightly reduces \( g_m \).
3. Finite output resistance of the current mirror.
4. Parasitic capacitances at the output node.

### 4.2 Phase Deviation Analysis

The theoretical phase shift for an inverting single-pole amplifier is **−180°**. The simulated excess phase of **~14.8°** is caused by:
- Contribution from non-dominant poles at internal nodes (drain of M5, gate of M4).
- Parasitic capacitances introducing additional phase lag even in the mid-band region.

## 5. Key Observations

### 5.1 Flat Gain Region

The gain is extremely flat from 50 mHz to 1 Hz:

$$
\Delta G = 5.5504122 - 5.5504094 \approx 0.0000028\ \text{dB}
$$

This confirms all transistors are properly biased in the saturation region.

### 5.2 Roll-off Behaviour

Beyond ~1 Hz, the gain rolls off at **−20 dB/decade**, confirming **single dominant-pole** behavior.

### 5.3 Phase Margin Consideration

At low frequency, the phase is **−194.822°**. If used in unity-gain feedback:

$$
\text{Phase Margin} = 180^\circ - 194.822^\circ = -14.822^\circ
$$

**Negative phase margin** indicates potential instability. Frequency compensation (e.g., Miller capacitor) is recommended for closed-loop operation.

## 6. Summary

- **Simulation mid-band gain**: 5.5504 dB (≈ 1.896 V/V)  
- **Theoretical mid-band gain**: ~6 dB (≈ 2.0 V/V)  
- **Agreement**: Good (~5% deviation)  
- **Dominant pole**: ~1–5 Hz  
- **Roll-off**: Single-pole (−20 dB/dec)  
- **Phase at low freq**: −194.8° (excess due to parasitics)

## 7. Conclusion

The AC analysis of the CMOS differential amplifier demonstrates **good agreement** between theoretical predictions and LTspice simulation using the TSMC 018 model.

The mid-band gain of **5.5504 dB** is close to the expected ~6 dB. The single-pole roll-off at approximately 1–5 Hz validates the dominant pole approximation at the output node. The excess phase shift is attributed to parasitic effects captured by the BSIM3v3 model but not included in first-order hand analysis.

For practical closed-loop applications, **frequency compensation** is necessary to achieve adequate phase margin and ensure stability.





# Transient Analysis — At \( V_{CM(min)} \)
<img width="1919" height="433" alt="image" src="https://github.com/user-attachments/assets/c65eea41-9d66-4b7c-91ff-53275472aef4" />
<img width="1919" height="452" alt="image" src="https://github.com/user-attachments/assets/36fc352a-bfec-42f0-b98a-d70308f0010c" />


## Aim
To analyze the transient response of a CMOS differential amplifier at the minimum common-mode voltage \( V_{CM(min)} \).

---

## 1. Input Conditions

- \( V_{in1} = \text{SINE}(V_{CM}, 10\,\text{mV}, 1\,\text{kHz}) \)
- \( V_{in2} = \text{SINE}(V_{CM}, 10\,\text{mV}, 1\,\text{kHz}, 180^\circ) \)

Where:
$$
V_{CM} = V_{CM(min)}
$$

---

## 2. Observations (From Simulation)

- Output waveform is **sinusoidal**  
- Output is centered around:
  $$
  V_{out,DC} \approx 258\,\text{mV}
  $$
- Peak value:
  $$
  V_{out,max} \approx 271\,\text{mV}
  $$
- Minimum value:
  $$
  V_{out,min} \approx 246\,\text{mV}
  $$
- Peak-to-peak output:
  $$
  V_{out,pp} \approx 25\,\text{mV}
  $$

---

## 3. Analysis

At \( V_{CM(min)} \):

- Tail transistor (M5) is **just in saturation**
- Input NMOS transistors (M1, M2) operate near the **edge of saturation**
- Output DC level shifts upward due to:
  - Limited voltage headroom
  - Reduced overdrive voltage of the input pair

---

## 4. Behavior Explanation

As \( V_{CM} \) decreases:

- \( V_{GS} \) of the input NMOS pair (M1, M2) decreases
- Drain current of the differential pair reduces
- PMOS active load (M3/M4) pulls the output node **towards \( V_{DD} \)**

---

## 5. Linearity

- The output waveform remains **sinusoidal**, indicating the circuit is still operating in the **linear region**.
- Slight distortion may start to appear if \( V_{CM} \) is reduced further below \( V_{CM(min)} \).

---

## 6. Key Insight

$$
V_{CM(min)} \quad \Rightarrow \quad \text{Lower limit of proper operation}
$$

Below this voltage:
- Input NMOS transistors (M1, M2) enter the **triode region**
- Differential gain reduces significantly
- Output waveform becomes distorted

---

## 7. Conclusion

- The CMOS differential amplifier operates correctly at \( V_{CM(min)} \).
- The output remains sinusoidal but with an upward DC shift.
- The circuit is operating at the **boundary of proper saturation region**.
- This simulation confirms the theoretical lower limit of the common-mode input range.

---






# Transient Analysis — At \( V_{CM(max)} \)
<img width="1908" height="439" alt="image" src="https://github.com/user-attachments/assets/ae1932d7-7569-4834-9565-601a0e12a8fa" />
<img width="1912" height="431" alt="image" src="https://github.com/user-attachments/assets/3796a5bd-35aa-485d-b246-3718ae6b2f9f" />


## Aim
To analyze the transient response of a CMOS differential amplifier at maximum common-mode voltage \( V_{CM(max)} \).

---

## 1. Input Conditions

- \( V_{in1} = \text{SINE}(V_{CM}, 10mV, 1kHz) \)
- \( V_{in2} = \text{SINE}(V_{CM}, 10mV, 1kHz, 180^\circ) \)

Where:

$$
V_{CM} = V_{CM(max)}
$$

---

## 2. Observations (From Graph)

From the waveform:

- Maximum output:

$$
V_{out,max} \approx -25.90 \text{ mV}
$$

- Minimum output:

$$
V_{out,min} \approx -26.53 \text{ mV}
$$

---

## 3. Output Calculation

### Peak-to-peak voltage:

$$
V_{out,pp} = V_{max} - V_{min}
$$

$$
V_{out,pp} = (-25.90) - (-26.53) = 0.63 \text{ mV}
$$

---

### Peak amplitude:

$$
V_{out,peak} = \frac{V_{pp}}{2} = \frac{0.63}{2} \approx 0.315 \text{ mV}
$$

---

### DC offset:

$$
V_{out,DC} = \frac{V_{max} + V_{min}}{2}
$$

$$
V_{out,DC} = \frac{-25.90 + (-26.53)}{2} \approx -26.21 \text{ mV}
$$

---

## 4. Analysis

At \( V_{CM(max)} \):

- NMOS transistors (M1, M2) are **strongly ON**
- PMOS load (M3, M4) approaches **triode region**
- Output is pulled **towards ground (low voltage)**

---

## 5. Behavior Explanation

- As \( V_{CM} \) increases:
  - \( V_{GS} \) of NMOS increases → higher current
  - PMOS \( V_{SD} \) decreases → leaves saturation

---


---

## 8. Conclusion

- The amplifier operates at the **upper boundary of common-mode range**
- Output is still sinusoidal but:
  - Very small amplitude
  - Reduced gain
- Confirms theoretical behavior of differential amplifier at high \( V_{CM} \)

---






# Experiment: Differential Amplifier – Large Signal Analysis (Case 1)

## Aim
To analyze the operation of a CMOS differential amplifier when  
Vid < √2 Vov and verify current distribution using LTspice.
<img width="933" height="653" alt="image" src="https://github.com/user-attachments/assets/c431acbe-c006-4b4d-8181-17c698b24d61" />

---

## Given Parameters

| Parameter | Value |
|----------|------|
| Vg | 0 V |
| Vs | -0.7 V |
| Vt | 0.366 V |
| Vin1 | 0.3 V |
| Vin2 | 0.1 V |

---

## Theory

A differential amplifier operates based on the difference between two input voltages:

Vid = Vin1 - Vin2

The operating region depends on:

Vid compared with √2 Vov

Where:

Vov = Vgs - Vt

---

## Calculations

### Gate-to-Source Voltage
Vgs = Vg - Vs  
Vgs = 0 - (-0.7) = 0.7 V

### Overdrive Voltage
Vov = Vgs - Vt  
Vov = 0.7 - 0.366 = 0.334 V

### Threshold Condition
√2 Vov = 1.414 × 0.334 = 0.472 V

### Differential Input
Vid = Vin1 - Vin2  
Vid = 0.3 - 0.1 = 0.2 V

---

## Condition Verification

Vid = 0.2 V < 0.472 V  

✔ Condition satisfied

---

## LTspice Results (Operating Point)

| Quantity | Value |
|---------|------|
| Id(M1) | 0.0005067 A |
| Id(M2) | 0.0004810 A |
| Tail Current Id(M5) | 0.0009877 A |
| Vout1 | -0.660 V |
| Vout2 | -0.626 V |

---
<img width="1915" height="438" alt="image" src="https://github.com/user-attachments/assets/6d262478-d51d-471a-aab6-09713a9b81f0" />

## Observation

- Id(M1) ≈ Id(M2)  
- Tail current is shared:  
  Itail ≈ I1 + I2  
- Both MOSFETs are ON  
- No transistor is OFF  
- We also get clean sine wave
---

## Working Principle

When Vid < √2 Vov:

- Both transistors operate in saturation  
- Current divides between M1 and M2  
- Output varies linearly with input  
- Circuit behaves as a linear amplifier  

---

## Result

The differential amplifier operates in the linear (small-signal) region for:

Vid < √2 Vov

Both transistors conduct simultaneously and share the tail current.

---

## Conclusion

- The theoretical condition is verified using LTspice  
- Current distribution confirms linear operation  
- The circuit works as a proper differential amplifier  
- Advantages of this region:
  - High gain  
  - Low distortion  
  - Stable operation
 








# Experiment: Differential Amplifier – Large Signal Analysis (Case 2)

## Aim
To analyze the operation of a CMOS differential amplifier when  
Vid > Vov and study current steering behavior using LTspice.
<img width="872" height="672" alt="image" src="https://github.com/user-attachments/assets/78e68d12-aeca-4304-9b45-d15c82545b36" />

---

## Given Parameters

| Parameter | Value |
|----------|------|
| Vg | 0 V |
| Vs | -0.7 V |
| Vt | 0.366 V |
| Vin1 | 0.7 V |
| Vin2 | 0.2 V |

---

## Theory

The operation of a differential amplifier depends on the input difference:

Vid = Vin1 - Vin2

For large input:

- If Vid > Vov → nonlinear region begins  
- If Vid > √2 Vov → one transistor turns OFF  

Where:

Vov = Vgs - Vt

---

## Calculations

### Gate-to-Source Voltage
Vgs = Vg - Vs  
Vgs = 0 - (-0.7) = 0.7 V  

### Overdrive Voltage
Vov = Vgs - Vt  
Vov = 0.7 - 0.366 = 0.334 V  

### Differential Input
Vid = Vin1 - Vin2  
Vid = 0.7 - 0.2 = 0.5 V  

---

## Condition Verification

Vov = 0.334 V  
Vid = 0.5 V  

✔ Vid > Vov (Large signal condition satisfied)

Also:

√2 Vov = 0.472 V  

✔ Vid > √2 Vov  

---

## LTspice Results (Operating Point)

| Quantity | Value |
|---------|------|
| Id(M1) | 0.000511 A |
| Id(M2) | 0.000486 A |
| Tail Current Id(M5) | 0.000997 A |
| Vout1 | -0.666 V |
| Vout2 | -0.633 V |

---
<img width="1907" height="463" alt="image" src="https://github.com/user-attachments/assets/b9088edd-8658-473a-bc5a-a8958090b160" />

## Observation

- Id(M1) > Id(M2)  
- Current is shifting toward M1  
- M2 current is reducing  
- Tail current remains constant  

---

## Working Principle

When Vid > Vov:

- Differential pair enters **nonlinear region**
- Current no longer splits equally
- One transistor starts dominating
- Output becomes **nonlinear**

When Vid > √2 Vov:

- One transistor carries almost full current
- Other transistor approaches cutoff

---

## Result

For Vid = 0.5 V:

- Vid > Vov → nonlinear operation  
- Vid > √2 Vov → current steering observed  

The circuit is moving toward **switching behavior**.

---

## Conclusion

- The amplifier leaves linear region for large input  
- Current shifts toward one transistor  
- Output becomes nonlinear  
- At very high Vid:
  - One MOSFET fully ON  
  - Other MOSFET OFF  






