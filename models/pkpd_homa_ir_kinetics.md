# Pharmacokinetic / Pharmacodynamic (PK/PD) HOMA-IR Differential Model

## 1. Dose-Response Hill Equation
Cellular transduction efficiency per daily treatment session is governed by a modified Hill activation function:

$$E(P_{\text{focal}}) = \begin{cases} 0 & \text{if } P_{\text{focal}} < P_{\text{thresh}} \\ E_{\max} \cdot \frac{(P_{\text{focal}} - P_{\text{thresh}})^\gamma}{P_{50}^\gamma + (P_{\text{focal}} - P_{\text{thresh}})^\gamma} & \text{if } P_{\text{focal}} \ge P_{\text{thresh}} \end{cases}$$

### Parameter Constants
* $P_{\text{thresh}} = 100.0\text{ kPa}$ (Minimum activation pressure)
* $P_{50} = 130.0\text{ kPa}$ (Pressure for half-maximal effect)
* $E_{\max} = 1.0$ (Normalized max efficacy)
* $\gamma = 2.5$ (Hill cooperativity exponent)

---

## 2. Longitudinal HOMA-IR Ordinary Differential Equation (ODE)
The daily rate of change in HOMA-IR score $H(t)$ across $t \in [0, 30]$ days is integrated using:

$$\frac{dH(t)}{dt} = -k_{\text{eff}} \cdot E(P_{\text{focal}}) \cdot \big(H(t) - H_{\text{target}}\big) + k_{\text{reg}} \cdot \big(H_{\text{base}} - H(t)\big)$$

### Integration Parameters
* $H(0) = H_{\text{base}} = 5.84 \pm 1.16$ (Baseline population score)
* $H_{\text{target}} = 1.50$ (Target healthy baseline)
* $k_{\text{eff}} = 0.12\text{ day}^{-1}$ (Therapeutic rate constant)
* $k_{\text{reg}} = 0.01\text{ day}^{-1}$ (Endogenous physiological rebound rate)
