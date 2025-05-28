---
title: "Sixth Order Elliptic Band Reject Filter"
date: 2025-05-28
categories: [engineering, filters]
tags: [electronics, signal-processing]
layout: single
---

## Requirements

Make an elliptic rejection filter for 1khz, 6pole (plus zeros) with -40dB as +/- 1.5% of 1khz.

## Synthesis of Detailed Requirements

The detailed requirements given in Table 1 are synthesized from the requirement statement.

### Table 1: Detailed Requirements

| Parameter | Value | Unit | Parameter Description |
|-----------|--------|------|----------------------|
| F0 | 1000 | Hz | Center Frequency |
| PRW | 0.5 (assumed) | dB | Pass Band Ripple Width |
| K | 1 (assumed) | - | Pass Band Gain |
| BW | 133.32 (assumed) | Hz | Band Width |
| F1 | 985 | Hz | Lower stop band edge frequency |
| F2 | 1015 | Hz | Upper stop band edge frequency |
| MSL | 40 | dB | Minimum Stop band attenuation |

## Mathematical Analysis

The resistance values can be calculated using:

$$R_1 = \frac{1}{K\beta\omega_0C_1}$$

$$R_2 = KR_1$$

$$R_3 = \frac{1}{\sqrt{\gamma\omega_0C_1}}$$

Where:
- $\omega_0$ is the center frequency in rad/s
- $K$ is the pass band gain
- $\beta$ and $\gamma$ are filter coefficients

The transfer function for this sixth-order elliptic filter is:

$$H(s) = \frac{N(s)}{D(s)}$$

This filter provides excellent stopband attenuation with minimal passband ripple.