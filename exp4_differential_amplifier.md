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


