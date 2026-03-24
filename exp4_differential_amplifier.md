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

This ensures all transistors operate in saturation and the amplifier works correctly.

---

