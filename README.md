# A Versatile System for Hall Effect Measurements at High Temperature

This paper, "A versatile system for Hall effect measurements at high temperature" by Murat Gunes et al., published in *Measurement Science and Technology* (2017), details the design and operation of a novel system for measuring the Hall effect in materials at elevated temperatures. The key innovation is the use of a rotating Halbach array magnet, which allows for fast, continuous, and versatile measurements under various conditions.

## Principle of Operation

The system is designed to overcome common challenges in high-temperature Hall effect measurements, such as thermal gradients, thermoelectric voltages (Seebeck effect), and measurement speed.

The core of the setup is a **donut-shaped Halbach magnet array**. This configuration produces a strong (1 T) and homogeneous magnetic field in the central bore. The magnet is mounted on a motorized stage, allowing it to be rotated at controlled speeds (up to ~2 Hz) or fixed at specific angles. This rotation enables the application of a DC or an AC magnetic field to the sample simply by controlling the motor.

The sample is mounted on a holder that can be heated up to 773 K and is placed within the magnet's bore. The system supports multiple measurement modes by combining DC or AC magnetic fields with either DC or AC electrical currents supplied to the sample.

* **DC Field Mode**: The magnet is rotated to a series of fixed angles. The Hall voltage shows a cosine dependence on the angle between the magnetic field and the sample normal. By plotting the measured voltage against the cosine of the angle, the Hall coefficient can be extracted from the slope. This method is quick, with a full set of measurements taking only a few seconds.
* **AC Field Mode**: The magnet is rotated continuously at a constant frequency.
    * With a **DC current**, the Hall voltage becomes an AC signal at the rotation frequency of the magnet, which can be sensitively detected using a lock-in amplifier referenced to the magnet's position. This filters out DC offsets.
    * With an **AC current** (at frequency $\omega_1$) and an AC magnetic field (at frequency $\omega_2$), the Hall voltage appears at the sum ($\omega_1 + \omega_2$) and difference ($\omega_1 - \omega_2$) frequencies. Lock-in detection at these sideband frequencies provides a powerful method for noise and offset rejection.

The system's ability to perform measurements in seconds allows for the continuous monitoring of the Hall coefficient as a function of temperature during a single thermal ramp, which is a significant advantage over traditional point-by-point measurements that require long stabilization times at each temperature. The paper demonstrates the system's effectiveness by presenting results for platinum (Pt) film, germanium (Ge), and the thermoelectric material BiCuSeO.

## Equations

The paper presents the following equations to describe the physical principles and measurement techniques:

1.  **General Electric Field Equation**: The electric field ($\vec{E}$) in a material under the influence of a magnetic field is given by:
    ```
    \vec{E} = \rho_{\perp}\vec{j} + \vec{n}(\vec{j}\cdot\vec{n})(\rho_{||} - \rho_{\perp}) + \rho_{H}\vec{n}\times\vec{j}
    ```
    where $\vec{j}$ is the current density, $\vec{n}$ is the unit vector in the direction of the magnetic field, $\rho_{||}$ and $\rho_{\perp}$ are the resistivities parallel and perpendicular to the field, and $\rho_{H}$ is the Hall resistivity.

2.  **Measured Hall Voltage**: For an isotropic sample, the measured voltage ($V_H$) across the Hall contacts is dependent on the orientation of the magnetic field:
    ```
    V_{H} = \frac{\mu_{H}\rho}{d}IB\cos\psi + \frac{C\mu_{H}^{2}\rho}{2d}IB^{2}\sin(2\varphi)\sin^{2}\psi
    ```
    where $I$ is the current, $B$ is the magnetic field strength, $d$ is the sample thickness, $\rho$ is the resistivity, $\mu_H$ is the Hall mobility, $\psi$ is the angle between the sample normal and the magnetic field, and $\varphi$ is the in-plane angle between the current density and the projection of the magnetic field. The second term represents the planar Hall effect.

3.  **AC/AC Measurement Inputs**: In the AC field/AC current mode, the current ($I$) and magnetic field ($H$) are described as sinusoidal functions:
    ```
    I = I_{0}\cos(\omega_{1}t + \varphi)
    ```
    ```
    H = H_{0}\cos(\omega_{2}t)
    ```
    where $\omega_1$ and $\omega_2$ are the angular frequencies of the current and field, respectively.

4.  **Resultant Hall Voltage in AC/AC Mode**: The product of the AC current and AC field results in a Hall voltage ($V_H$) with sum and difference frequency components:
    ```
    V_{H} = \frac{R_H}{2d}I_{0}H_{0}\{\cos[(\omega_{1} - \omega_{2})t + \varphi] + \cos[(\omega_{1} + \omega_{2})t + \varphi]\}
    ```
    where $R_H$ is the Hall coefficient and $d$ is the sample thickness.

5.  **Hall Coefficient Calculation**: The Hall coefficient ($R_H$) can be calculated from the measured Hall voltage ($V_H$):
    ```
    R_{H} = \frac{2d V_{H}}{IH}
    ```
    where $I$ and $H$ are the amplitudes of the current and field, and $V_H$ is the voltage amplitude measured at the sideband frequency.