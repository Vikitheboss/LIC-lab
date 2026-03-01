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
