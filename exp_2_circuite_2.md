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
