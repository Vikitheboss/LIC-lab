


<h1 style="font-size:30px;">Experiment-1</h1>


<h1 style="font-size:25px;">Common Source amplifier analysis-1</h1>


This experiment shows the ac,dc and transient analysis of cs amplifier


<h1 style="font-size:25px;">Abstract</h1>
In this experiment, we analyze a Common Source Amplifier using DC, AC, and transient analysis. DC analysis determines the biasing condition, AC analysis studies frequency response, and transient analysis observes time-domain signal amplification and gain.


<h1 style="font-size:25px;">Theory</h1>
# Common Source (CS) Amplifier – Theory

## Introduction

A **Common-Source (CS) amplifier** is a widely used MOSFET amplifier configuration in which:

- The input is applied to the **gate**
- The output is taken from the **drain**
- The **source** acts as the common terminal

It provides voltage amplification by varying the drain current ($I_D$) in response to changes in the gate-to-source voltage ($V_{GS}$).

The output signal is **180° out of phase** with the input signal, meaning the amplifier produces an inverted output.

The CS amplifier has:

- High input impedance (because gate current is nearly zero)
- Moderate to high output impedance

---

## Conditions for Proper Operation

For correct amplification, the MOSFET must operate in the **saturation region**.

The required conditions are:

1. $V_{GS} \geq V_{th}$  
   → To turn the transistor ON  

2. $V_{DS} > V_{GS} - V_{th}$  
   → To keep the transistor in saturation  

3. The input signal $v_{in}$ must be small  
   → To ensure small-signal operation  

4. Proper biasing and correct selection of $R_D$  
   → To obtain stable operation and sufficient voltage gain  

---

## Drain Current in Saturation Region

In the saturation region, the drain current is given by:

$$
I_D = \frac{1}{2} k_n (V_{ov})^2
$$

where,

$$
V_{ov} = V_{GS} - V_{th}
$$

$k_n$ = Process transconductance parameter  

---

## Small-Signal Voltage Gain

The voltage gain of a CS amplifier is:

$$
A_v = -g_m R_D
$$

where,

$$
g_m = \frac{2 I_D}{V_{ov}}
$$

The negative sign indicates **phase inversion**.

<h1 style="font-size:25px;">Circuit</h1>
<img width="1112" height="625" alt="image" src="https://github.com/user-attachments/assets/05f10269-010b-45c5-ad54-f1731b5a9df5" />
# Experiment Specifications – Common Source (CS) Amplifier

## Given Design Requirements

| Parameter | Symbol | Value | Unit | Description |
|------------|---------|--------|------|-------------|
| Supply Voltage | VDD | 1.2 | V | DC power supply |
| Maximum Power | Pmax | ≤ 0.4 | mW | Power constraint |
| Load Capacitance | CL | 0.5 | pF | Output load |
| NMOS Channel Length | Ln | 360 | nm | Technology parameter |
| Technology Node | — | 180 | nm | CMOS process |
| Simulation Tool | — | LTspice | — | Design environment |

---

## Derived Parameter (From Power Constraint)

| Parameter | Formula | Calculated Value | Unit |
|------------|----------|------------------|------|
| Maximum Drain Current | ID ≤ Pmax / VDD | ≤ 0.333 | mA |



<h1 style="font-size:25px;">Dc Analysis</h1>
## DC Analysis in Common Source (CS) Amplifier

DC analysis is performed to determine the biasing condition (operating point) of the MOSFET.

It calculates the steady-state values of $I_D$, $V_{GS}$, and $V_{DS}$ to ensure the transistor operates in the **saturation region** for proper and distortion-free amplification.
<img width="1744" height="766" alt="image" src="https://github.com/user-attachments/assets/fe63a2b0-17df-4906-bb21-6e6ff78ee0d3" />
# Simulated DC Operating Point Results

| Parameter | Symbol | Simulated Value | Unit |
|------------|---------|----------------|------|
| Supply Voltage | VDD | 1.2 | V |
| Input Voltage | Vin | 0.9 | V |
| Output Voltage | Vout | 0.5897 | V |
| Drain Current | ID | 0.339 | mA |
| Current through RD | I(RD) | 0.339 | mA |
| Supply Current | I(VDD) | 0.339 | mA |

---

## Power Calculation

P = VDD × ID  

P = 1.2 × 0.339 mA  

P = 0.4068 mW
