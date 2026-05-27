# Visibility-State Computing (VSC) — 雾度计算

**Author:** Mao Guanghui (毛广辉)

**Concept Origin:** 2026-05-23

**Status:** Conceptual Stage v1.0

**License:** MGOVL v2.0 (Mao Guanghui Open View License)

---

## 中文概念说明

### 起源

2026年5月23日清晨，观察到窗外雾蒙蒙的能见度景象，触发以下核心问题：

> **能见度本身，能否作为一种信息计算的物理载体？**

### 核心定义

雾度计算（Visibility-State Computing，VSC）是一种以大气或流态介质中的**光散射率（能见度）状态变化**作为信息单元的非冯·诺依曼物理计算范式。

- **雾盲态（Fog-Blind State）**：高散射、低能见度状态，对应信息的未定态或高熵态
- **能见态（Visibility State）**：低散射、高透射状态，对应计算的输出结果
- **计算周期（Computation Window）**：同一物理介质中，从能见态弛豫至雾盲态（或反向）的时间常数 τ

### 物理机制

**信息写入：** 调控气溶胶粒径分布、密度或折射率，改变介质对光的散射特性（Mie散射 / Rayleigh散射域），使能见度 V(t) 发生受控变化。

**信息读出：** 以能见度阈值检测器读取连续模拟值 V(t)，经阈值量化后输出计算结果。

**计算时钟：** 弛豫时间常数 τ 由介质物理属性决定，无需外部时钟电路。

### 一阶关系模型

```
V(t) = V_min + (V_max - V_min) · exp(-t / τ)

V(t)    — t 时刻的能见度
V_max   — 初始能见态（清晰）
V_min   — 终止雾盲态（模糊）
τ       — 介质弛豫时间常数（计算周期基准）
```

### 与现有计算范式的区别

| 范式 | 信息载体 | VSC区别 |
|------|---------|--------|
| 流体计算（1960s） | 气/液压差 | VSC使用散射率/透射率而非压力 |
| 储层计算 | 水波、气泡动态 | VSC有明确的能见度读出机制 |
| 光子计算 | 固态介质中的光场 | VSC使用流态介质（气溶胶/大气）|
| 量子计算 | 量子叠加态 | VSC为经典物理连续值计算 |

### 与光影芯片的关系

光影芯片（Optical Shadow Chip）：固态介质中光场分布的**空间计算**
雾度计算（VSC）：流态介质中光透射窗口的**时序计算**

两者共同构成以**光的可见性状态为信息单元的计算族（Visibility-Class Computing）**。

---

## English Concept Statement

### Origin

On the morning of May 23, 2026, observing foggy conditions outside prompted the following core question:

> **Can visibility itself serve as the physical carrier of information computation?**

### Core Definition

Visibility-State Computing (VSC) is a non-von Neumann physical computing paradigm that uses **changes in the light scattering rate (visibility) within atmospheric or fluid media** as information units.

The paradigm exploits a physical truth that has never been framed computationally: visibility is not merely an environmental observation — it is a measurable, controllable, time-varying scalar that carries retrievable information. The fog was never just weather. It was an unread register.

- **Fog-Blind State**: High-scattering, low-visibility — undefined or high-entropy information state
- **Visibility State**: Low-scattering, high-transmittance — the computed output
- **Computation Window**: Relaxation time constant τ of the medium between states

### Physical Mechanism

**Write:** Modulate aerosol particle size distribution, density, or refractive index to produce controlled changes in optical scattering coefficient.

**Read:** A visibility threshold detector continuously samples V(t); quantization against a threshold extracts the computed output.

**Clock:** The relaxation time constant τ is an intrinsic property of the medium. No external clock circuit required. The physics is the timing.

### First-Order Model

```
V(t) = V_min + (V_max - V_min) · exp(-t / τ)

V(t)    — Visibility at time t
V_max   — Initial clear state (high transmittance)
V_min   — Terminal fog-blind state (high scattering)
τ       — Medium relaxation time constant (computation window)
```

### Paradigm Positioning

| Paradigm | Information Carrier | VSC Distinction |
|----------|-------------------|----------------|
| Fluidic Computing (1960s) | Pneumatic/hydraulic pressure | VSC uses scattering rate, not pressure |
| Reservoir Computing | Water waves, bubble dynamics | VSC has explicit visibility readout |
| Photonic Computing | Light fields in solid media | VSC operates in fluid/aerosol media |
| Quantum Computing | Quantum superposition states | VSC is classical continuous-value computing |
| **VSC (this work)** | **Fluid-medium optical scattering rate** | **No prior naming; first conceptual disclosure** |

### Relationship to Optical Shadow Chip

Optical Shadow Chip: Spatial computing via light field distribution in solid-state media.
VSC: Temporal computing via light transmittance windows in fluid media.

Together they constitute: **Visibility-Class Computing** — computing systems where the fundamental information unit is the observable state of light.

---

## Interactive Simulator · 交互式仿真器

**Live Demo:** https://maomaoati-coder.github.io/Visibility-State-Computing/

Adjust microchannel parameters (L, w, h, η, ΔP, Kn) and observe the V(t) relaxation curve evolve in real time.
The simulation demonstrates the clockless physical relaxation property of VSC:
τ is determined entirely by the medium — no external clock circuit required.

## Prior Art Record

**SHA256 (document):**

**v1.0 concept ·** 2ed2a2b80f7fe0ee91c75adf905e9d1434628deb4e1f2219030f4b12503f3c2a

**v1.1 framework ·** 9446df823bbfe37c427aa3ed3e9b9ba0f9ba42d8403e889c306af63d6b11c394

**Timestamp:** 2026-05-23T02:04:25Z (UTC)

**Inventor:** Mao Guanghui (毛广辉)

**First Public Disclosure:** This README commit

**Repository:** github.com/maomaoati-coder/Visibility-State-Computing

**Pages:** maomaoati-coder.github.io/Visibility-State-Computing/

---

## License

MGOVL v2.0 — Mao Guanghui Open View License

Viewing and citation with attribution permitted.
Reproduction, adaptation, and commercial use prohibited without written authorization from Mao Guanghui.

© 2026 Mao Guanghui. All rights reserved.
