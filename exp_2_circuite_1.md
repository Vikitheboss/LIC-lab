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
