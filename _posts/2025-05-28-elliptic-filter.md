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


## Filter Topology Selection

The sixth-order elliptic band reject filter implementation employs a Biquad filter topology. This topology choice is driven by two key advantages: first, biquads naturally support the introduction of zeros, which are fundamental to elliptic filter characteristics; second, they offer superior tuning flexibility during implementation.

## Design Approach
A sixth-order band reject filter architecture requires six poles and three zeros. The design leverages a well-established transformation technique where a sixth-order band reject elliptic filter can be synthesized using the filter coefficients of a third-order elliptic low-pass filter.
The required filter coefficients are sourced from "A Handbook of Active Filters" by D.E. Johnson, J.R. Johnson, and H.P. Moore. Specifically, we utilize the coefficients for a third-order low-pass elliptic filter characterized by 0.5 dB passband ripple width (PRW) and 40 dB minimum stopband attenuation (MSL) (ref. page 191 of the book)

### Table 2: coefficients for a third-order low-pass elliptic filter with 0.5dB PRW and 40 dB MSL

| MSL | TW     | A        | B        | C        |
| --- | ------ | -------- | -------- | -------- |
| 40  | 1.7115 | 9.629215 | 0.580638 | 1.146209 |
|     |        |          |          | 0.659093 |

The filter coefficients A, B, and C in the first row are for the “second order” stage and the filter coefficient C, in the second row is for the “first order” stage.

A second order circuit of Biquad filter topology is shown in Figure 1. The ports of input "v_in" and output "BR_out1" is shown in Figure 1. The reference designators of the components used in Figure 1 will be referred in the calculation of their values. These reference designators are having suffix "a" to represent that this is for the first stage. The reference designators of the second and third stage will be suffixed with "b" and “c” respectively. 

## Figure 1: Circuit diagram of a second order Biquad filter topology 
![2nd Order Elliptic Filter Circuit](/assets/images/2025-05-28-elliptic-filter/image1.png)

The band reject filter that is obtained from the coefficients of “3rd order” low pass filter is of “6th order”. This is because, the "one" second order stage of the low pas filter will yield "two" second order stages of band reject filter and "one first order” stage of the low pass filter will yield "one second order” stage of band reject filter.

The Figure 1 implements one second order stage of the 6th order band reject filter. The same circuit is repeated two more times and cascaded in series as shown in Figure 2 to form a sixth order band reject filter. In Figure 2, input is provided at v_in and output is obtained at BR_out1. The output of first stage BR_out1 is input to the second stage. The output of the second stage BR_out2 is input to the v_in of the third stage. The complete output of the 6th order band reject filter is obtained at the output of the third stage and it is designated as BR_out3. The reference designators of the components in stage 1, 2 and 3 are the same except for the suffix "a", "b" or "c" for the first, second and third stages respectively. 

### Figure 2: Sixth order band reject elliptic filter composed of three second order stages 

![6th Order Elliptic Filter Circuit](/assets/images/2025-05-28-elliptic-filter/image2.png)

The values of the components of the 6th order elliptic band reject filter are calculated in following steps: 

## Quality Factor and angular frequency 

The Quality Factor "Q" is the ratio of the center frequency to band width of the notch. It determines the selectivity of the filter. The values for quality factor and angular frequency are calculated in Table 3.

| Parameter         | Formula           | Value  | Unit      |
| ----------------- | ----------------- | ------ | --------- |
| Quality Factor    | $Q=\frac{f_0}{BW}$   | 7.5    | Unit less |
| Angular frequency | $W_0=2πf_0$ | 6283.2 | Hz        |

## 4th order stage of band reject filter corresponding to 2nd order stage of low pass filter 

The factors A2, E1 and D1 are calculated from the filter coefficients A, B, C of the second order stage of elliptic low pass filter together with the "Q" (quality factor) of the filter to be designed. These three factors are common for the two second order stages of band reject filter corresponding to the one second order stage of low pass filter. The formulas and values for A2, E1 and D1 are given in Table 4.



<!-- ## Mathematical Analysis -1 

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

This filter provides excellent stopband attenuation with minimal passband ripple. -->