


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

# Transient Analysis of Common Source (CS) Amplifier

## Introduction

Transient analysis is performed to study the time-domain behavior of the Common Source (CS) amplifier. It shows how the output voltage changes with respect to time when an input signal is applied.

## Purpose of Transient Analysis

The main objectives are:

- To observe signal amplification over time
- To verify phase inversion (180° phase shift)
- To measure voltage gain from input and output waveforms
- To check signal distortion and stability




## Voltage Gain Measurement

Voltage gain is calculated using peak values:

$$
A_v = \frac{V_{out}}{V_{in}}
$$

Since the CS amplifier inverts the signal:

$$
A_v = - \frac{V_{out}}{V_{in}}
$$
<img width="1444" height="706" alt="image" src="https://github.com/user-attachments/assets/81bb4054-4f3e-4d0f-896e-c1d5a4c78de6" />
<p align="center">
   
  <img width="800" alt="Transient Analysis Output" src="https://github.com/user-attachments/assets/81bb4054-4f3e-4d0f-896e-c1d5a4c78de6">
</p>
<p align="center">
# Transient Analysis – Common Source Amplifier

---

## 1. Input Waveform (V_in)

<p align="center">
  <img width="900" alt="Input Waveform V(in)" src="https://github.com/user-attachments/assets/8d3a9caf-73c1-4026-804d-87cf406049fd">
</p>

**Fig 1:** Transient response of input signal $V_{in}$.

### Measured Input Values

| Parameter | Value | Unit |
|------------|--------|------|
| DC Offset | 0.9 | V |
| Peak Voltage | 0.9496 | V |
| Minimum Voltage | 0.85 | V |
| Input Amplitude | 50 | mV |
| Frequency | 1 | kHz |

---

---
# Transient Analysis – Common Source Amplifier

---

## 1. Input Waveform (V_in)
<img width="1899" height="816" alt="image" src="https://github.com/user-attachments/assets/8f00d64f-1634-4327-abf5-ef728ea4d68e" />


<p align="center">
  

**Fig 1:** Transient response of input signal $V_{in}$.

---

## Measured Input Values (From Cursor)

| Parameter | Value | Unit |
|------------|--------|------|
| DC Offset | 0.9 | V |
| Peak Voltage | 0.9495 | V |
| Minimum Voltage | 0.85 | V |
| Input Amplitude | 50 | mV |
| Frequency | 1 | kHz |
| Cursor Time | 4.2414 | ms |
| Cursor Voltage | 949.51 | mV |

---

---

## 2. Output Waveform (V_out)

<p align="center">
  <img width="1916" height="1002" alt="image" src="https://github.com/user-attachments/assets/dc13583f-e57d-450d-9f74-5ca44b1c8aa3" />

</p>

**Fig 2:** Transient response of output signal $V_{out}$.

---

## Measured Output Values (From Cursor)

| Parameter | Value | Unit |
|------------|--------|------|
| Peak Voltage | 684.887 | mV |
| Minimum Voltage | 497.988 | mV |
| DC Level | 0.5897 | V |
| Peak-to-Peak Voltage | 186.9 | mV |
| Output Amplitude | 93.45 | mV |

---

## Peak-to-Peak Calculation

$$
V_{pp} = V_{max} - V_{min}
$$

$$
V_{pp} = 684.887\,mV - 497.988\,mV
$$

$$
V_{pp} \approx 186.9\,mV
$$

---
## Voltage Gain Calculation

Input peak-to-peak voltage:

$$
V_{in(pp)} = 0.9495 - 0.85
$$

$$
V_{in(pp)} = 99.5\,mV
$$

Output peak-to-peak voltage:

$$
V_{out(pp)} = 186.9\,mV
$$

Voltage gain:

$$
A_v = \frac{V_{out(pp)}}{V_{in(pp)}}
$$

$$
A_v = \frac{186.9}{99.5}
$$

$$
A_v \approx 1.88
$$

Since the Common Source amplifier produces phase inversion:

$$
A_v \approx -1.88
$$

### Reason for Negative Gain

The gain is negative because the Common Source amplifier inverts the signal.  
When the input voltage increases, the drain current increases, causing a larger voltage drop across $R_D$, which reduces the output voltage.  
Thus, the output is 180° out of phase with the input.
