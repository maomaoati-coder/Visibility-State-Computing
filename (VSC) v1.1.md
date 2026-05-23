# VISIBILITY-STATE COMPUTING (VSC) — 雾度计算
## Concept Brief & Physical Framework · VSC-PROT-2026-001

**Inventor:** Mao Guanghui (毛广辉) · Independent Inventor
**Document ID:** VSC-PROT-2026-001
**Version:** v1.1
**First Disclosure:** 2026-05-23T02:04:25Z (UTC)
**License:** MGOVL v2.0 — Mao Guanghui Open View License

> *"The fog was never just weather. It was an unread register."*
> — Mao Guanghui, 2026-05-23

---

## I. PARADIGM DEFINITION

**Visibility-State Computing (VSC)** is a non-von Neumann, analog physical computing paradigm that utilizes the dynamically shifting extinction coefficient and optical transmittance of a fluidic aerosol medium as the primary information carrier.

Unlike *Fluidic Computing* (which modulates pneumatic/hydraulic pressure vectors) or standard *Photonic Computing* (which relies on deterministic propagation through static solid-state lattices), VSC operationalizes the **macroscopic visibility gradient** resulting from multi-scale Mie and Rayleigh scattering as a continuous-value state transition function.

Three fundamental states are defined:

| State | Physical Description | Information-Theoretic Mapping | VSC Abstraction |
|---|---|---|---|
| Fog-Blind (雾盲态) | High scattering, low transmittance | Maximum entropy / undefined state | Reset State S_max |
| Visibility (能见态) | Low scattering, high transmittance | Coherent field readout | Output State S_min |
| Relaxation Window | Dynamical transition between states | State transition execution space | Computation Cycle T_calc |
| V(t) scalar | Transmittance integral over path L | Continuous analog register | Output Value |

---

## II. FIRST-ORDER PHYSICAL MODEL

### 2.1 Visibility Function

```
V(t) = V_min + (V_max - V_min) · exp(-t / τ)

  V_max  — Initial clear state (high transmittance)
  V_min  — Terminal fog-blind state (high scattering)
  τ      — Medium relaxation time constant (computation window baseline)
```

### 2.2 Extinction Coefficient and Computation Cycle

Beer-Lambert law mapping:

```
T(λ, t) = exp[ -β_ex(t) · L ]

  T(λ,t) — Spectral transmittance at wavelength λ and time t
  β_ex   — Volumetric extinction coefficient [m⁻¹]
           = β_scatter(t) + β_absorb  (Mie + Rayleigh contributions)
  L      — Optical path length [m]
```

Computation cycle T_calc:

```
T_calc = τ · ln[ (V_max - V_min) / (ε · V_max) ]

  ε — Contrast threshold of sensor array (typically 0.02–0.05)
```

**Key property:** T_calc is determined entirely by the physical medium. No external electronic clock tree is required. The physics is the timing.

### 2.3 Input Modulation — Mie Integral

```
β_ex(t) = ∫ Q_ext(r, λ, m) · π·r² · n(r, t) dr

  Q_ext(r,λ,m) — Mie extinction efficiency
                  (particle radius r, wavelength λ, complex refractive index m)
  n(r, t)      — Particle size distribution at time t  [m⁻³ m⁻¹]

Write operation: control n(r,t) via PZT ultrasonic atomization,
                 micro-injection, or thermal field modulation
```

---

## III. ON-CHIP IMPLEMENTATION — MICROFLUIDIC AEROSOL ARCHITECTURE

To compress macroscopic fog evolution timescales (hours) to sub-millisecond computation windows, VSC adopts a **Microfluidic Aerosol Chip** architecture. At microchannel scale, τ is governed by fluid-mechanical boundary conditions, not meteorological dynamics.

### 3.1 One-Cell Logic Unit

```
                 ┌─────────────────────────────────────────────────┐
                 │         VSC MICROFLUIDIC LOGIC CELL             │
                 └─────────────────────────────────────────────────┘

 [Input A] ──→ PZT Ultrasonic Transducer A ──┐
                                              ├──→ [Blending Chamber]
 [Input B] ──→ PZT Ultrasonic Transducer B ──┘         │
                                                        ▼ (aerosol generation)
 [Coherent   ───────────────────────────────→ [Optical Path Channel]
  Light λ]                                             │
                                                        ▼ (Mie decoupling)
 [Output Y]  ←── PD Array (Spatial Contrast) ←─────────┘
```

### 3.2 Relaxation Time Constant at Microchannel Scale

```
τ = η · L² / (ΔP · w · h · Kn)

  η   — Carrier gas dynamic viscosity  [Pa·s]
  L   — Channel length  [m]
  ΔP  — Micro-pressure differential  [Pa]
  w   — Channel width  [m]
  h   — Channel height  [m]
  Kn  — Knudsen number = λ_mfp / L_char
         (slip-flow correction for mean free path at micro-scale)

Tuning L/w ratio → different intrinsic τ per cell
→ cascaded temporal logic without external synchronization
```

### 3.3 Spatial Interference Contrast Readout

```
C(t) = (I_max - I_min) / (I_max + I_min)

  I_max, I_min — Extrema of spatial interference fringe intensity

V(t) ∝ C(t)  [monotonic under fixed geometry and λ]
```

This mechanism enables VSC to serve as the **direct downstream stage of the Optical Shadow Chip**: the spatial light field output is received at the VSC fluid interface, converting spatial photonic computation into temporal transmittance-window computation in-situ.

---

## IV. VISIBILITY-CLASS COMPUTING — UNIFIED FRAMEWORK

| Branch | Medium | Computation Mode | Optimized For |
|---|---|---|---|
| Optical Shadow Chip | Solid-state / liquid crystal | Spatial light field modulation | High-frequency deterministic tensor operations |
| **VSC (this work)** | **Fluid aerosol / microfluidic** | **Temporal transmittance window** | Time-series modeling, non-equilibrium thermo simulation, chaotic seed generation |

**Visibility-Class Computing (VCC):** Computing systems in which the fundamental information unit is the observable state of light propagating through a controllable medium — spanning solid-state spatial computation to fluid-state temporal computation.

---

## V. PROVENANCE LOG AND PRIOR ART DECLARATION

| Field | Value |
|---|---|
| Inventor | Mao Guanghui (毛广辉) |
| Affiliation | Independent (no institutional backing) |
| Concept Origin | Morning observation of atmospheric fog, 2026-05-23 |
| First Disclosure | 2026-05-23T02:04:25Z (UTC) |
| SHA256 · v1.0 | `2ed2a2b80f7fe0ee91c75adf905e9d1434628deb4e1f2219030f4b12503f3c2a` |
| SHA256 · v1.1 | `9446df823bbfe37c427aa3ed3e9b9ba0f9ba42d8403e889c306af63d6b11c394` |
| Repository | github.com/maomaoati-coder/Visibility-State-Computing |

**Recommended commit message:**
```
feat: VSC-PROT-2026-001 v1.1 — microfluidic implementation layer + full physical model
```

---

## VI. LICENSE

**MGOVL v2.0 — Mao Guanghui Open View License**

Viewing and citation with attribution to Mao Guanghui (毛广辉) is permitted.
Reproduction, adaptation, derivative works, and commercial use are **prohibited** without written authorization from Mao Guanghui.

© 2026 Mao Guanghui. All rights reserved.
