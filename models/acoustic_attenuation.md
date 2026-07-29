# Acoustic Propagation & Multi-Layer Tissue Attenuation Model

## 1. Multi-Layer Attenuation Formula
Acoustic wave propagation through heterogeneous biological tissue layers (skin, fat, muscle) is defined by exponential decay:

$$P(d) = P_0 \cdot \exp\left( -\sum_{i=1}^{N} \alpha_i(f) \cdot x_i \right) \cdot \Gamma_{\text{misalign}}$$

Where:
* $P_0$: Initial pressure at the transducer surface ($\text{kPa}$).
* $\alpha_i(f) = \alpha_0 \cdot f^n$: Frequency-dependent tissue attenuation ($\text{dB/cm/MHz}$).
* $x_i$: Thickness of tissue layer $i$ ($\text{cm}$).
* $\Gamma_{\text{misalign}}$: Alignment penalty due to off-axis beam displacement $\Delta r$:

$$\Gamma_{\text{misalign}} = \exp\left( -\left(\frac{\Delta r}{w_0}\right)^2 \right)$$

Where $w_0$ is the $6\text{ dB}$ beam focal waist radius ($\approx 1.5\text{ mm}$).

---

## 2. Parameter Distribution Table

| Tissue Layer | Nominal Thickness ($x_i$) | Stress Thickness ($x_i$) | Attenuation Coeff ($\alpha_0$) |
| :--- | :--- | :--- | :--- |
| **Epidermis/Dermis** | $0.20 \pm 0.05\text{ cm}$ | $0.25\text{ cm}$ | $1.20\text{ dB/cm/MHz}$ |
| **Subcutaneous Fat** | $0.50 - 4.00\text{ cm}$ | $4.00 - 6.50\text{ cm}$ | $0.40 - 0.75\text{ dB/cm/MHz}$ |
| **Muscle / Fascia** | $0.80 \pm 0.20\text{ cm}$ | $1.50\text{ cm}$ | $1.00\text{ dB/cm/MHz}$ |
