# HT-Halbach

This program is used for the measurement of Hall effect at high temperature and it was written in 2013-2014, the version described here was updated in 2023. The method is extensively described in a paper by Murat Gunes et al., published in *Measurement Science and Technology* (2017). For more details the reader can consult that article.

---

## Overview and Principle of Operation

The system is designed to overcome common challenges in high-temperature Hall effect measurements, such as thermal gradients and thermoelectric voltages. The key point of this system, which is used in my lab nowadays, is the use of a rotating permanent NdFeB **Halbach magnet array** which allows for measurements under various conditions. For this setup, we employ a lab-made furnace inserted in a sample holder maintained under vacuum, heated internally, and inserted in "donut" of the magnet. The sample is mounted on a holder that can be heated up to 773 K. Our setup has holder of 28 mm diameter; obviously larger bores will be more comfortable to work with but will be more much expensive.

This magnet is mounted on a motorized stage (Owis Gmbh), allowing it to be rotated at controlled speeds (up to ~2 Hz) or fixed at specific angles. This rotation enables the application of either a DC or an AC magnetic field to the sample. The system supports multiple measurement modes by combining DC or AC magnetic fields with either DC or AC electrical currents.

**DC Field Mode** 
The magnet is rotated to a series of fixed angles. The Hall voltage shows a cosine dependence on the angle between the magnetic field and the sample normal. By fitting the measured voltage against the cosine of the angle, the Hall coefficient is extracted from the slope. This method is very fast, with a full set of measurements taking few tens of seconds.

**AC Field Mode** 
The magnet is rotated continuously at a constant frequency, typically 1 Hz. A position detector is fed to the Reference-in of a lock-in amplifier, which is highly effective at filtering out DC offsets and noise. This can be done with either a DC current or a dual-AC method (AC current and AC field) for maximum noise rejection. This method takes longer, few minutes for one measurement, and is to be used for low mobility samples.

---

## Equations

The main physical equation for a material under the influence of a magnetic field is :

$$
    \vec{E} = \rho_{\perp}\vec{j} + \vec{n}(\vec{j}\cdot\vec{n})(\rho_{||} - \rho_{\perp}) + \rho_{H}\vec{n}\times\vec{j} 
$$

**Measured Hall Voltage** 
For an isotropic sample, the measured voltage ($V_H$) across the Hall contacts is dependent on the orientation of the magnetic field:

$$
V_{H} = \frac{\mu_{H}\rho}{d}IB\cos\psi + \frac{C\mu_{H}^{2}\rho}{2d}IB^{2}\sin(2\varphi)\sin^{2}\psi
$$

**AC/AC Measurement Inputs**

In the AC field/AC current mode, the current ($I$) and magnetic field ($H$) are described as sinusoidal functions:

$$ I = I_{0}\cos(\omega_{1}t + \varphi); \quad H = H_{0}\cos(\omega_{2}t) $$

The product of the AC current and AC field results in a Hall voltage ($V_H$) with sum and difference frequency components:

$$ V_{H} = \frac{R_H}{2d}I_{0}H_{0}\{\cos[(\omega_{1} - \omega_{2})t + \varphi] + \cos[(\omega_{1} + \omega_{2})t + \varphi]\} $$

The Hall coefficient ($R_H$) can be calculated from the measured Hall voltage ($V_H$)

$$ R_{H} = \frac{2d V_{H}}{IH} $$

This method is not used in the last version of the program.

---

The system has been extensively tested and used in the last 10 years. The only problem we have is the frequent break of the high temperature heater, probably from a poor design. Some commercial instruments are available.

### Computer program
The program available here is very specific, so unless you have an Owis motor, the same current sources (Keithely 6220 or 6221) and Lock-in amplifier, it is not that useful.

Examples of measurements are given below.

* **Platinum (Pt) Film**
    * At room temperature, the system measured an average Hall coefficient of $-0.21 \times 10^{-12} \ \Omega \cdot \text{cm/Gauss}$, which is consistent with reported literature values.
    * It successfully extracted a tiny Hall signal (on the order of $5 \times 10^{-8}$ V) from a much larger offset voltage ($>7.7 \times 10^{-6}$ V), showcasing its sensitivity.
    * The measurements proved to be highly stable over a 48-hour period.

* **Germanium (Ge) Single Crystal**
    * A p-type Ge crystal was tested using all six measurement modes, with all configurations yielding consistent results around $1.9 \times 10^{-5} \  \Omega \cdot \text{cm/Gauss}$.
    * During a high-temperature measurement from 300 K to 625 K, data points were acquired every 5 seconds while the temperature was ramped continuously.
    * The results clearly showed the material's transition from p-type to intrinsic (n-type dominant) behavior at higher temperatures.

* **BiCuSeO (Thermoelectric Material)**
    * The system was used to measure this challenging low-mobility material, where the offset voltage ($10^{-5}$ V) was about 100 times larger than the Hall signal ($10^{-7}$ V).
    * The room temperature carrier concentration of $2 \times 10^{21} \, \text{cm}^{-3}$ matched results from a commercial system that uses a 9T magnet.
    * High-temperature measurements showed the carrier concentration increasing up to $2.6 \times 10^{21} \, \text{cm}^{-3}$ at 650 K.

### Comparison of AC and DC Field Modes 

The key difference between the modes is how the magnetic field is applied and how the signal is detected.

#### **DC Field Mode**
* **Principle**: The magnet is moved to a series of fixed angular positions, selected by the user, and a measurement is taken at each static point.
* **Signal Extraction**: The Hall constant is determined from the slope of a line when plotting the measured Hall voltage against the cosine of the angle ($\psi$).
* **Current**: In this version this method can be used with a DC current.


#### **AC Field Mode**
* **Principle**: The magnet rotates continuously at a constant frequency (e.g., 0.5-2 Hz), producing a sinusoidal AC magnetic field.
* **Signal Extraction**: This mode relies on a lock-in amplifier that uses the magnet's rotation as its reference frequency. The lock-in amplifier isolates this signal, rejecting DC offsets.
* **Key Advantage**: The primary benefit is superior rejection of parasitic DC offset voltages, which is crucial for measuring low-mobility samples with very small Hall signals.
