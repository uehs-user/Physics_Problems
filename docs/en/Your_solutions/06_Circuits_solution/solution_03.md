# Mixed Circuit Analysis

The total equivalent resistance of the circuit is **$3.81\ \Omega$** (or exactly **$\frac{80}{21}\ \Omega$**).

---

### **Circuit Parameters**
* **Individual Resistor Value ($R$):** $5\ \Omega$
* **Total Resistors:** $8$

---

### **Step-by-Step Simplification**

#### **1. Inner Parallel Loops**
The left section of the circuit splits into two separate paths that reconnect at the top-middle junction:
* **Path 1 (Top-Left Loop):** Two resistors in series.
  $$R_1 = 5\ \Omega + 5\ \Omega = 10\ \Omega$$
* **Path 2 (Inner-Middle Loop):** Three resistors in series.
  $$R_2 = 5\ \Omega + 5\ \Omega + 5\ \Omega = 15\ \Omega$$

Combining these two parallel paths:
$$R_{\text{left}} = \frac{R_1 \times R_2}{R_1 + R_2} = \frac{10 \times 15}{10 + 15} = \frac{150}{25} = 6\ \Omega$$

---

#### **2. Upper Main Branch**
The simplified left section ($R_{\text{left}}$) connects directly in series with the far-right branch, which contains two vertical resistors:
* **Right Branch Resistance:** 
  $$R_{\text{right}} = 5\ \Omega + 5\ \Omega = 10\ \Omega$$
* **Total Upper Branch Resistance:** 
  $$R_{\text{upper}} = R_{\text{left}} + R_{\text{right}} = 6\ \Omega + 10\ \Omega = 16\ \Omega$$

---

#### **3. Total Equivalent Resistance ($R_{\text{eq}}$)**
The entire upper branch ($R_{\text{upper}}$) is in parallel with the single horizontal resistor ($5\ \Omega$) running along the very bottom wire:

$$R_{\text{eq}} = \frac{R_{\text{upper}} \times R}{R_{\text{upper}} + R}$$

$$R_{\text{eq}} = \frac{16 \times 5}{16 + 5} = \frac{80}{21}\ \Omega \approx 3.81\ \Omega$$
