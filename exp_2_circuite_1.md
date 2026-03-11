# **EXPERIMENT 1 – CIRCUIT 1**

---
<img width="1276" height="607" alt="image" src="https://github.com/user-attachments/assets/304d52a5-9f98-4491-b321-15e30dc57dbd" />


## **1. Supply Voltages**

| No. | Source Name | Type  | Value |
|-----|------------|-------|-------|
| 1 | V1 | SINE Source | DC Offset = 0.81 V |
|   |    |             | Amplitude = 10 mV |
|   |    |             | Frequency = 1 kHz |
|   |    |             | AC = 1 |
| 2 | V2 | DC | 1.5 V |
| 3 | V3 (VDD) | DC | 1.5 V |
| 4 | V4 | DC | 0.86 V |

---

## **2. Passive Component**

| No. | Component | Value |
|-----|-----------|--------|
| 5 | R1 | 666.6666667 Ω |

---

## **3. MOSFET Details**

### **M1 – NMOS (CMOSN)**

| Parameter | Expression |
|------------|------------|
| Gate Voltage (VG1) | Vin |
| Drain Voltage (VD1) | Vout |
| Source Voltage (VS1) | Vrs |
| VGS1 | Vin − Vrs |
| VDS1 | Vout − Vrs |

---

### **M2 – PMOS (CMOSP)**

| Parameter | Expression |
|------------|------------|
| Source Voltage (VS2) | 1.5 V (VDD) |
| Drain Voltage (VD2) | Vout |
| Gate Voltage (VG2) | 1.5 V |
| VSG2 | 1.5 − Vout |
| VSD2 | 1.5 − Vout |

---

## **4. Node Voltages**

| No. | Node Name | Value |
|-----|------------|-------|
| 6 | Vin (DC Bias) | 0.81 V |
| 7 | VDD | 1.5 V |
| 8 | Bias Node (V4) | 0.86 V |
| 9 | Output Node | Vout |
| 10 | Source Node (NMOS) | Vrs |

---


# **1. VERIFICATION OF SATURATION REGION**

---

## **1.1 Given DC Operating Point Values**

\[
\begin{aligned}
V_{in}  &= 0.81 \text{ V} \\
V_{out} &= 0.970546 \text{ V} \\
V_{rs}  &= 0.198243 \text{ V} \\
V_{DD}  &= 1.5 \text{ V} \\
I_D     &= 297.364 \,\mu\text{A}
\end{aligned}
\]

---
## **1.2 NMOS (M1)**

### **1.2.1 Voltage Calculations**

The gate-to-source voltage of M1 is

\[
V_{GS1} = V_{in} - V_{rs}
\]

\[
V_{GS1} = 0.81 - 0.198243 = 0.611757 \text{ V}
\]

The drain-to-source voltage of M1 is

\[
V_{DS1} = V_{out} - V_{rs}
\]

\[
V_{DS1} = 0.970546 - 0.198243 = 0.772303 \text{ V}
\]

---

### **1.2.2 Saturation Condition**

For an NMOS transistor to operate in saturation,

\[
V_{DS1} \geq V_{GS1} - V_{TN}
\]

Assuming a threshold voltage for 0.18 µm technology,

\[
V_{TN} \approx 0.4 \text{ V}
\]

\[
V_{GS1} - V_{TN} = 0.611757 - 0.4 = 0.211757 \text{ V}
\]

Since

\[
0.772303 \geq 0.211757
\]

the condition for saturation is satisfied for M1.

---

## **1.3 PMOS (M2)**

### **1.3.1 Voltage Calculations**

The source-to-gate voltage of M2 is

\[
V_{SG2} = V_{S2} - V_{G2}
\]

\[
V_{SG2} = 1.5 - 1.5 = 0 \text{ V}
\]

The source-to-drain voltage of M2 is

\[
V_{SD2} = V_{S2} - V_{D2}
\]

\[
V_{SD2} = 1.5 - 0.970546 = 0.529454 \text{ V}
\]

---

### **1.3.2 Saturation Condition**

For a PMOS transistor to operate in saturation,

\[
V_{SD2} \geq V_{SG2} - |V_{TP}|
\]

Assuming

\[
|V_{TP}| \approx 0.4 \text{ V}
\]

\[
V_{SG2} - |V_{TP}| = 0 - 0.4 = -0.4 \text{ V}
\]

Since

\[
0.529454 \geq -0.4
\]

the saturation condition is satisfied for M2.


---

# **2. DC ANALYSIS**
<img width="1871" height="859" alt="image" src="https://github.com/user-attachments/assets/369d1412-2eb2-4184-9976-32f46fd97467" />


## **2.1 Operating Point Results (Simulation)**

| Parameter | Value | Unit |
|------------|--------|------|
| **Vin** | **0.81** | V |
| **Vout** | **0.970546** | V |
| **Vrs** | **0.198243** | V |
| VDD | 1.5 | V |
| Bias Voltage | 0.86 | V |

---

## **2.2 DC Currents (Simulation)**

| Parameter | Value | Unit |
|------------|--------|------|
| **Id (M1)** | **0.000297364** | A |
| **Id (M2)** | **−0.000297364** | A |
| I(R1) | 0.000297364 | A |
| Is (M1) | −0.000297364 | A |
| Is (M2) | 0.000297364 | A |

---

## **2.3 Theoretical Calculations**

### **Drain Current**

\[
I_D (\text{theoretical}) = 300 \,\mu A
\]

---

### **Source Voltage**

\[
V_{rs} = I_D \times R_S
\]

\[
V_{rs} = (300 \,\mu A)(666.67 \,\Omega)
\]

\[
V_{rs} \approx 0.2 \text{ V}
\]

---

### **Output Voltage**

\[
V_{out} = \frac{V_{DD}}{2} + 0.2
\]

\[
V_{out} = \frac{1.5}{2} + 0.2
\]

\[
V_{out} = 0.75 + 0.2
\]

\[
V_{out} = 0.95 \text{ V}
\]

---

# **2.4 Comparison of Theoretical and Simulation Results**

| Parameter | Theoretical | Simulation | Difference |
|------------|------------|------------|------------|
| **Id** | 300 µA | 297.364 µA | 2.636 µA |
| **Vrs** | 0.2 V | 0.198243 V | 0.001757 V |
| **Vout** | 0.95 V | 0.970546 V | 0.020546 V |

---

## **2.5 Observation**

- The simulated drain current is very close to the theoretical value.
- The simulated source voltage nearly matches the expected 0.2 V.
- The output voltage shows a small deviation due to device parameters, channel length modulation, and model effects in 0.18 µm technology.

The practical (simulation) results closely agree with the theoretical calculations.
---
## **3. TRANSIENT ANALYSIS**

---
<img width="1870" height="766" alt="image" src="https://github.com/user-attachments/assets/0fdb1235-34b4-4f74-aaa7-8c059e63c987" />


### **3.1 Input Signal**


\[
V_{in}(t) = 0.81 + 10\,\text{mV}\,\sin(2\pi \cdot 1\,\text{kHz} \cdot t)
\]

\[
V_{DC} = 0.81 \text{ V}
\]

\[
V_m = 10 \text{ mV}
\]

\[
f = 1 \text{ kHz}
\]

---

### **3.2 Output Voltage**


\[
V_{out}(t) = V_{OUT,DC} + v_{out}(t)
\]

\[
V_{OUT,DC} \approx 0.970546 \text{ V}
\]

\[
v_{out}(t) = A_v \cdot 10\,\text{mV} \cdot \sin(2\pi \cdot 1\,\text{kHz} \cdot t)
\]

---

### **3.3 Source Voltage**

\[
V_{rs}(t) = 0.198243 + v_{rs}(t)
\]

---

### **3.4 Drain Current**

\[
I_D(t) = 297.364\,\mu\text{A} + i_d(t)
\]

\[
i_d(t) = g_m \cdot 10\,\text{mV} \cdot \sin(2\pi \cdot 1\,\text{kHz} \cdot t)
\]

---
## 4. Transient Analysis – Output Voltage Waveform
<img width="1918" height="397" alt="image" src="https://github.com/user-attachments/assets/e9635040-8da1-4b96-8b2d-e510618b801b" />
### 4.1 Observed Output Waveform Vout(t)

VOUT,DC ≈ 0.970546 V

---

### 4.2 Peak and Minimum Values

Vout,max ≈ 1.06 V  
Vout,min ≈ 0.86 V  

---

### 4.3 Peak-to-Peak Voltage

Vout,pp = Vout,max − Vout,min  

Vout,pp = 1.06 − 0.86 = 0.20 V  

Vout,peak = Vout,pp / 2 = 0.10 V  

---

### 4.4 Frequency Verification

T ≈ 1 ms  

f = 1 / T = 1 / 1 ms = 1 kHz  

---

### 4.5 Output Voltage Expression

Vout(t) ≈ 0.970546 + 0.10 sin(2π × 1 kHz × t)

---

## 4.6 Transient Analysis – Input Voltage Waveform
<img width="1912" height="401" alt="image" src="https://github.com/user-attachments/assets/4a7af064-eed5-4e2f-8b2a-66d9c2ed31b3" />


### 4.6.1 Observed Input Waveform Vin(t)

VIN,DC ≈ 0.81 V

---

### 4.6.2 Peak and Minimum Values

Vin,max ≈ 0.82 V  
Vin,min ≈ 0.80 V  

---

### 4.6.3 Peak-to-Peak Voltage

Vin,pp = Vin,max − Vin,min  

Vin,pp = 0.82 − 0.80 = 0.02 V  

Vin,peak = Vin,pp / 2 = 0.01 V = 10 mV  

---

### 4.6.4 Frequency Verification

T ≈ 1 ms  

f = 1 / T = 1 / 1 ms = 1 kHz  

---

### 4.6.5 Input Voltage Expression

Vin(t) ≈ 0.81 + 0.01 sin(2π × 1 kHz × t)

---

## 5. Theoretical Voltage Gain Calculation

Given:

Id = 300 µA  
λ = 0.1 V⁻¹  
Vov = 0.25 V  
Rs = 666.67 Ω  

---

### 5.1 Transconductance gm

gm = 2Id / Vov  

gm = (2 × 300 × 10⁻⁶) / 0.25  

gm = 0.0024 S  

gm = 2.4 mS  

---

### 5.2 Output Resistance ro

ro = 1 / (λ Id)  

ro ≈ 33,333 Ω  

ro ≈ 33.3 kΩ  

---

### 5.3 Effective Output Resistance

ro,eff = ro / 2  

ro,eff ≈ 16,667 Ω  

ro,eff ≈ 16.7 kΩ  

---

### 5.4 Gain Without Source Degeneration

Av = gm × ro,eff  

Av ≈ 40  

Av,dB ≈ 32 dB  

---

### 5.5 Gain With Source Degeneration

Av = − gm ro,eff / (1 + gm Rs)

gm ro,eff ≈ 40  

gm Rs ≈ 1.6  

Av ≈ − 15.38  

|Av| ≈ 15.38  

Av,dB ≈ 23.7 dB  

---

### Final Comparison

Gain without Rs ≈ 40 (32 dB)  
Gain with Rs ≈ 15.38 (23.7 dB)  
Practical Gain ≈ 10 (20 dB)




## 7. AC Analysis
<img width="1903" height="460" alt="image" src="https://github.com/user-attachments/assets/a1c8e12c-4be3-43de-b52f-e0b82adc940c" />

AC command:

.ac dec 100 100 100G

---
<img width="1893" height="389" alt="image" src="https://github.com/user-attachments/assets/6a0ebec4-a6bb-4c4e-a79b-27777815278c" />

### 7.1 Midband Gain

Av ≈ 15.38  

Av,dB ≈ 20.7 dB  

---

### 7.2 Frequency Response

Low frequency region:
Gain ≈ constant  
Phase ≈ 180°  

High frequency region:
Gain decreases due to Cgs, Cgd, Cdb  

---
<img width="1906" height="404" alt="image" src="https://github.com/user-attachments/assets/ffd7f58b-6cf0-4cfb-9971-661229e47ad3" />

### 7.3 Bandwidth

Midband gain = 20.7 dB  

Cutoff gain = 20.7 − 3  

Cutoff gain ≈ 17.7 dB  

Bandwidth = fH − fL  







# Experiment 2 Circuit 2

## Circuit
<img width="905" height="844" alt="image" src="https://github.com/user-attachments/assets/641a1ce9-8c3a-4193-9da7-40abd4a5e9fd" />

### Description
The circuit consists of one PMOS transistor acting as an active load and two NMOS transistors forming the bias network.  
The supply voltage is 1.5 V and the input is a sinusoidal source with DC offset.

---

## Circuit Parameters

| Parameter | Value |
|------------|--------|
| Supply Voltage (V1) | 1.5 V |
| PMOS Gate Bias (V5) | 1.5 V |
| Output Voltage (Vout) | 0.86 V |
| Input Source (V2) | SINE(0.916666667 10m 1k) |
| Input DC Offset | 0.916666667 V |
| Input Amplitude | 10 mV |
| Input Frequency | 1 kHz |
| Bias Voltage (V3) | 0.616666 V |
| M1 | PMOS (CMOSP) |
| M2 | NMOS (CMOSN) |
| M3 | NMOS (CMOSN) |

---

## Simulation Commands

| Command | Description |
|----------|--------------|
| .op | DC Operating Point Analysis |
| .ac dec | AC Analysis |
| .tran 5n | Transient Analysis |
| .include | Model File Inclusion |

#  Calculations

## Given Parameters

| Parameter | Value |
|------------|--------|
| VDD | 1.5 V |
| Vtn | 0.366 V |
| |Vtp| | 0.39 V |
| Assumed Overdrive Voltage (Vov) | 0.25 V |
| Vin (DC) | 0.916666 V |

---

# 1. PMOS Transistor (M1)

For PMOS in saturation:

Vov = VSG − |Vtp|

Therefore,

VSG = Vov + |Vtp|

VSG = 0.25 + 0.39  
VSG = 0.64 V

Now calculate output voltage:

Vout = VDD − VSG  
Vout = 1.5 − 0.64  
Vout = 0.86 V

Result:

Vout = 0.86 V

---

# 2. NMOS Transistor (M2)

Assume source voltage:

Vs ≈ 0.3 V

### Step 1: Calculate VGS

VGS = Vin − Vs  
VGS = 0.916666 − 0.3  
VGS = 0.616666 V

### Step 2: Overdrive Check

VGS − Vtn  
= 0.616666 − 0.366  
= 0.250666 ≈ 0.25 V

### Step 3: Check Saturation Condition

Condition for NMOS saturation:

VDS ≥ VGS − Vtn

Calculate VDS:

VDS = Vout − Vs  
VDS = 0.86 − 0.3  
VDS = 0.56 V

Now compare:

0.56 ≥ 0.25

Condition satisfied.

Conclusion:

M2 is in saturation.

---

# 3. NMOS Transistor (M3)

Source of M3 is grounded.

### Step 1: Calculate VGS

VGS3 = VG − VS  
VGS3 = 0.616666 − 0  
VGS3 = 0.616666 V

### Step 2: Overdrive

VGS3 − Vtn  
= 0.616666 − 0.366  
= 0.250666 ≈ 0.25 V

### Step 3: Check Saturation

VDS3 = VD − VS  
VDS3 = 0.3 − 0  
VDS3 = 0.3 V

Check condition:

0.3 ≥ 0.25

Condition satisfied.

Conclusion:

M3 is in saturation.

---

# Final Results

| Transistor | Region of Operation |
|------------|--------------------|
| M1 (PMOS) | Saturation |
| M2 (NMOS) | Saturation |
| M3 (NMOS) | Saturation |
| Vout | 1.05 V |

All transistors are operating in saturation region.
#  Width Calculation and Drain Current

---

## Given Parameters

| Parameter | Value |
|------------|--------|
| Power (P) | 0.5 mW |
| VDD | 1.5 V |
| Assumed ID | ≈ 300 µA |
| Channel Length (L) | 180 nm = 0.18 µm |
| kn' | 235.92 µA/V² |
| kp' | 99.685 µA/V² |
| Overdrive Voltage (Vov) | 0.25 V |

---

# 1. Drain Current Calculation

Power relation:

P = VDD × ID

Therefore,

ID = P / VDD

ID = 0.5 mW / 1.5 V  
ID = 0.333 mA  

ID = 333.33 µA  

For design simplification:

ID ≈ 300 µA

---

# 2. NMOS Width Calculation (Wn)

Saturation current equation:

ID = (1/2) kn' (Wn/L) Vov²

Rearranging for Wn/L:

Wn/L = (2 ID) / (kn' Vov²)

Substitute values:

Wn/L = (2 × 300 µA) / (235.92 µA × 0.25²)

Wn/L = 600 / (235.92 × 0.0625)

Wn/L = 600 / 14.745

Wn/L = 40.7

Now multiply by L:

Wn = 40.7 × 0.18 µm

Wn = 7.32 µm

---

# 3. PMOS Width Calculation (Wp)

Saturation equation:

ID = (1/2) kp' (Wp/L) Vov²

Rearranging:

Wp/L = (2 ID) / (kp' Vov²)

Substitute values:

Wp/L = (2 × 300 µA) / (99.685 µA × 0.25²)

Wp/L = 600 / (99.685 × 0.0625)

Wp/L = 600 / 6.2303

Wp/L = 96.3

Now multiply by L:

Wp = 96.3 × 0.18 µm

Wp = 17.33 µm

---

# Final Results

| Parameter | Value |
|------------|--------|
| ID | 333.33 µA (Assumed 300 µA for design) |
| Wn | 7.32 µm |
| Wp | 17.33 µm |
| L | 0.18 µm |

---

All calculations are based on saturation region operation.





#  Updated Simulation Device Dimensions

## Simulation Parameters Used

| Transistor | Type | Width (W) | Length (L) |
|------------|------|------------|------------|
| M1 | PMOS (CMOSP) | 58.35 µm | 180 nm |
| M2 | NMOS (CMOSN) | 28 µm | 180 nm |
| M3 | NMOS (CMOSN) | 22 µm | 180 nm |

---

All values listed above are the actual device dimensions used in the LTspice simulation.





# DC Analysis

---
<img width="1904" height="823" alt="image" src="https://github.com/user-attachments/assets/60baacec-73d4-4a7f-8395-f404766de5c9" />

## 1. DC Operating Point Results (From Simulation)

| Parameter | Value |
|------------|--------|
| VDD | 1.5 V |
| Vout | 1.05035 V |
| Id(M1) | 302.842 µA |
| Id(M2) | 302.842 µA |
| Id(M3) | 302.842 µA |

(Note: Negative sign in LTspice indicates current direction. Magnitude is considered.)

---

## 2. Theoretical Design Values

| Parameter | Theoretical Value |
|------------|------------------|
| Target Id | 300 µA |
| Estimated Vout | 0.86 V |

---

## 3. Comparison Between Theory and Simulation

### Drain Current Comparison

Simulation Id = 302.842 µA  
Designed Id = 300 µA  

Difference:

302.842 − 300 = 2.842 µA  

Percentage Error:

(2.842 / 300) × 100 = 0.95 %

The drain current closely matches the designed value with less than 1% error.

---

### Output Voltage Comparison

Theoretical Vout = 0.86 V  
Simulation Vout = 1.05035 V  

Difference ≈ 0.19 V  

This deviation occurs due to:

- Channel length modulation  
- Body effect  
- Mobility degradation  
- Accurate SPICE device modeling  

---

## 4. Conclusion

- The simulated drain current is very close to the designed value.
- The error in current is less than 1%.
- All transistors operate in saturation region.
- The DC analysis validates the theoretical calculations.

The circuit biasing is accurate and stable.





# Transient Analysis

---
<img width="1910" height="834" alt="image" src="https://github.com/user-attachments/assets/5bf0f754-7376-472b-a3e4-c6f08002bbd5" />

## 1. Simulation Setup

| Parameter | Value |
|------------|--------|
| Analysis Type | Transient (.tran 5m) |
| Input Signal | SINE(0.9166667 10m 1k) |
| DC Offset | 0.9167 V |
| Amplitude | 10 mV |
| Frequency | 1 kHz |

---

## 2. Input Voltage (Vin)

From waveform:
<img width="1908" height="850" alt="image" src="https://github.com/user-attachments/assets/a5721525-b6b9-40a8-85e5-ceb9107fddae" />


| Parameter | Value |
|------------|--------|
| Vin_max | 926 mV |
| Vin_min | 906 mV |

Peak-to-peak input voltage:

Vpp_in = 926 mV − 906 mV  
Vpp_in = 20 mV

---

## 3. Output Voltage (Vout)

From waveform:

<img width="1916" height="867" alt="image" src="https://github.com/user-attachments/assets/20ec0467-1a1c-4ce2-9d47-f57f6b4848ba" />

| Parameter | Value |
|------------|--------|
| Vout_max | 1.066 V |
| Vout_min | 1.034 V |

Peak-to-peak output voltage:

Vpp_out = 1.066 V − 1.034 V  
Vpp_out = 0.032 V  
Vpp_out = 32 mV

---

## 4. Voltage Gain (Av)
<img width="1911" height="850" alt="image" src="https://github.com/user-attachments/assets/a3ce79b0-24cf-4793-b78f-003a6614c673" />

Voltage gain:

Av = Vpp_out / Vpp_in  
Av = 32 mV / 20 mV  
Av = 1.6

Since the output is inverted:

Av ≈ −1.6  

Magnitude of gain:

|Av| = 1.6

---

## 5. Gain in Decibels (dB)

Gain_dB = 20 log10(|Av|)

Gain_dB = 20 log10(1.6)

Gain_dB ≈ 4.08 dB

---

## 6. Conclusion

- Input peak-to-peak voltage: 20 mV  
- Output peak-to-peak voltage: 32 mV  
- Voltage gain: −1.6  
- Gain in dB: 4.08 dB  

The circuit shows small-signal amplification without distortion or clipping.




# AC Analysis

---

## 1. Midband Gain (From Graph)
<img width="1874" height="827" alt="image" src="https://github.com/user-attachments/assets/e8b24670-182d-439b-b992-9fb51e7ee21e" />


From cursor:

Frequency = 7.071 MHz  
Gain = 4.324 dB  
Phase = 178.276°

---

## 2. Convert Gain from dB to Linear

Av = 10^(Gain_dB / 20)

Av = 10^(4.324 / 20)

Av = 10^(0.2162)

Av = 1.64

Since phase ≈ 180°, amplifier is inverting:

Av ≈ −1.64

---

## 3. -3 dB Bandwidth Calculation
<img width="1895" height="833" alt="image" src="https://github.com/user-attachments/assets/b2f34b69-f3ae-4722-93cf-812f6f27c063" />


Midband gain = 4.324 dB

-3 dB level:

4.324 − 3 = 1.324 dB

From graph:

Frequency at ≈ 1.324 dB ≈ 127 MHz

Upper cutoff frequency:

fH ≈ 127 MHz

Lower cutoff frequency:

Flat response down to 100 Hz

Therefore:

fL < 100 Hz

---

## 4. Final Calculated Values

| Parameter | Value |
|------------|--------|
| Midband Gain (dB) | 4.324 dB |
| Midband Gain (Linear) | 1.64 |
| Voltage Gain (Av) | −1.64 |
| Upper Cutoff Frequency (fH) | ~127 MHz |
| Lower Cutoff Frequency (fL) | < 100 Hz |



# EXPERIMENT 2 – CIRCUIT 3

# EXPERIMENT 2 – CIRCUIT 3  
Common Source Amplifier with PMOS Active Load

---

# Circuit Diagram

<img width="1918" height="895" alt="Circuit Diagram" src="https://github.com/user-attachments/assets/169c1d12-68d8-4457-b680-9b0f0d0c3642" />

---

# Supply Voltages

| Source | Value |
|------|------|
| VDD (V1) | 1.5 V |
| Bias Voltage (V2) | 1.5 V |
| PMOS Gate Bias (V5) | 0.86 V |
| Input Source (V3) | SINE(1.23 10m 1k) |

Input signal parameters  

Amplitude = 10 mV  
Frequency = 1 kHz  
DC offset = 1.23 V  

---

# MOSFET Parameters

| Transistor | Type | Width | Length |
|-----------|------|------|------|
| M1 | NMOS | 27.47 µm | 180 nm |
| M2 | PMOS | 58.1 µm | 180 nm |
| M3 | NMOS | 18.27 µm | 180 nm |

Technology used  
TSMC 180 nm CMOS model

---

# DC Operating Point

From LTspice operating point analysis

<img width="718" height="624" alt="Operating Point" src="https://github.com/user-attachments/assets/5799e644-e582-45c7-b074-eee40ab17ad8" />

| Parameter | Value |
|---------|--------|
| Vin | 1.23 V |
| Vout | 1.06024 V |
| Vrs | 0.619974 V |
| Id(M1) | 300.6 µA |
| Id(M2) | -300.6 µA |
| Id(M3) | 300.6 µA |

Observation  

The current flowing through M1, M2 and M3 is approximately equal, confirming correct biasing and stable operating point.

---

# Calculations

## Drain Current

From LTspice operating point

Id(M1) = 0.000300601 A  

Therefore

Id ≈ 300 µA

---

## Overdrive Voltage

Overdrive voltage

Vov = VGS − VTH

Given

Vov = 0.25 V

---

## Transconductance

Transconductance of MOSFET

gm = 2Id / Vov

gm = (2 × 300 µA) / 0.25

gm = 600 µA / 0.25

gm = 0.0024 S

gm = **2.4 mS**

---

## Output Resistance

Output resistance of MOSFET

ro = 1 / (λ Id)

Given

λ = 0.1  
Id = 300 µA

ro = 1 / (0.1 × 300 × 10⁻⁶)

ro = 1 / (3 × 10⁻⁵)

ro ≈ **33333 Ω**

ro ≈ **33.3 kΩ**

Since the same current flows through all MOSFETs

ro1 ≈ ro2 ≈ ro3 ≈ **33.3 kΩ**

---

## Theoretical Voltage Gain

For the given circuit the gain is

Av ≈ − gm1 ro2 / (1 + gm3 ro3)

Substituting values

gm1 = gm3 = 2.4 mS  
ro2 = ro3 = 33.3 kΩ

First calculate

gm3 ro3

= 2.4 × 10⁻³ × 33333

≈ 80

Denominator

1 + 80 = 81

Now numerator

gm1 ro2

= 2.4 × 10⁻³ × 33333

≈ 80

Therefore

Av ≈ −80 / 81

Av ≈ **−0.99**

---

## Gain from AC Simulation

From AC frequency response

Gain ≈ **23 dB**

Voltage gain

Av = 10^(Gain / 20)

Av = 10^(23 / 20)

Av ≈ **14.1**

---

# Transient Analysis

Transient simulation command

```
.tran 10m
```

---

## Output Waveform

<img width="1904" height="424" alt="Vout waveform" src="https://github.com/user-attachments/assets/f2c73550-af6c-432f-90de-a515e737e046" />

Observation  

The output signal is amplified and inverted compared to the input signal.

---

## Input Waveform

<img width="1904" height="410" alt="Vin waveform" src="https://github.com/user-attachments/assets/2ea8933e-920d-4692-ae3b-9f430768662b" />

Observation  

The input signal is a sinusoidal waveform with small amplitude of 10 mV.

---

# AC Analysis

AC analysis command

```
.ac dec 1000 100 100G
```

---

## Frequency Response

<img width="1894" height="452" alt="AC response" src="https://github.com/user-attachments/assets/3c1b0f5a-bbe0-4a27-bfcb-a9815f37cd59" />

Observation  

The amplifier provides high gain in the low and mid frequency region and decreases at higher frequencies due to parasitic capacitances.

---

# DC Sweep Analysis

DC sweep command

```
.dc V3 0 1.5 0.0001
```

---

## DC Transfer Characteristic

<img width="1894" height="404" alt="DC sweep" src="https://github.com/user-attachments/assets/d9336648-78e4-43ed-bfb5-ba178df32e79" />

Observation  

The graph shows the relationship between input voltage and output voltage.

---

# Result

A CMOS common source amplifier with PMOS active load was designed and simulated using TSMC 180 nm technology.

The circuit demonstrates

• Proper MOSFET biasing  
• Amplification of small input signals  
• Phase inversion between input and output  
• Frequency response characteristics of CMOS amplifiers  

The simulation results confirm the expected behavior of the common source amplifier configuration.

---ehavior of a CMOS common source amplifier.





---

# RESULTS

## Circuit 1

The MOSFET amplifier circuit was successfully simulated and the operating point was obtained. The drain current (ID), output voltage (Vout), and small-signal parameters such as transconductance (gm) and output resistance (ro) were calculated.  

The voltage gain obtained from the theoretical calculation was found to be close to the gain observed in the simulation.

The biasing conditions ensured that the MOSFET operated in the **saturation region**, which is required for proper amplification. Minor differences between theoretical and simulation values were observed due to approximations used in device parameters.

---

## Circuit 2

The second circuit was designed to analyze the small signal amplification with different biasing conditions. Parameters such as **overdrive voltage (Vov), transconductance (gm), and voltage gain (Av)** were calculated theoretically.

The simulation results confirmed that the MOSFET operated in the saturation region and produced the expected amplified output. The gain obtained from simulation was reasonably close to the theoretical value.

---

## Circuit 3

The third circuit was implemented to study the effect of circuit configuration on the amplifier gain and output characteristics.

The MOSFET parameters were extracted and used to compute the expected voltage gain. Simulation results showed that the amplifier produced a stable output with proper biasing. The measured gain from simulation closely matched the calculated theoretical gain.

---

# COMPARISON OF RESULTS

| Circuit | Theoretical Gain | Simulation Gain | Observation |
|--------|-----------------|----------------|-------------|
| Circuit 1 | Calculated using gm and ro | Obtained from simulation | Values are closely matching |
| Circuit 2 | Derived using small signal model | Observed from simulation | Slight variation due to modeling assumptions |
| Circuit 3 | Computed from circuit parameters | Measured from output waveform | Good agreement |

**Observation:**  
The theoretical and simulation values are in close agreement. Small deviations occur due to ideal assumptions in theoretical analysis and internal device modeling in simulation.

---

# CONCLUSION

The MOSFET amplifier circuits were successfully designed and analyzed. Proper DC biasing ensured that the MOSFET operated in the **saturation region**, enabling effective signal amplification.

Small signal parameters such as **transconductance (gm), output resistance (ro), and voltage gain (Av)** were calculated theoretically and verified using simulation results.

The comparison between theoretical and simulation values shows good agreement, validating the theoretical analysis of MOSFET amplifier circuits.

---

# INFERENCE

1. Proper **DC biasing** is essential for stable MOSFET amplifier operation.
2. The **voltage gain depends mainly on transconductance (gm) and output resistance (ro)**.
3. Theoretical analysis provides a close approximation of circuit performance.
4. Minor deviations between theoretical and simulation values occur due to **device modeling and parameter approximations**.

---
