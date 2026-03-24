# BCAM Array (SKY130)
## Introduction
This project covers the design, physical layout, and verification of three custom memory blocks using the SKY130 process: a 6T SRAM bit-cell, a 1-bit BCAM cell, and a 4-bit BCAM array. The work was split into two stages. In the first stage, each circuit was designed and simulated at the schematic level using Xschem and NGSpice to verify that the intended logic and storage behaviour worked as intended. In the second stage, a layout was designed for each block. Afterward, extraction, DRC and LVS checking, and post-extraction simulation were used to confirm that the design remained functional and correct.

## Testing and Verification Methodologies
The goal was to show that not only did each schematic work ideally, but also to ensure that the layout preserved the intended behavior. Hence, both waveform plots and .meas were used. The waveforms provide a visualization of the circuit operation, while the .meas statements translate those waveforms into quantifiable pass/fail.

Waveforms are important because they show the relationship between control signals and internal/output nodes. For example, from a waveform, it is possible to see that: the wordline (WL) turns on at the correct time, the bitlines (BL & BLB) or searchlines (SL & SLB) are driven to the intended values, and the storage or matchlines (ML & MLF) nodes respond accordingly.

However, a waveform isn't enough evidence that the circuit is correct because the visual interpretation is subjective. For instance, a node may appear “high enough” or “low enough” by eye without proving that it actually satisfies the required operating condition. Thus, .meas is used to provide numerical values.

For example, if ml_pre is the matchline voltage immediately before evaluation and ml_min is the minimum matchline voltage during evaluation, then
`.meas tran ml_drop PARAM='ml_pre - ml_min'`
computes the matchline discharge magnitude. Another statement, such as
`.meas tran match_ok PARAM='(ml_min > 0.9*VDD)'`
then converts that analog behavior into a logical verification result. If the minimum matchline voltage stays above the required threshold, match_ok returns 1; otherwise, it returns 0. 

## 1-bit BCAM Cell
### Xschem
![image](https://github.com/joez-7/BCAM-Array-SKY130/blob/7bfe0bfd765db0e6e3558b7feee1b7ae163b1694/images/bcam1.png)

### Layout
![image](https://github.com/joez-7/BCAM-Array-SKY130/blob/a957816dd77f1167cfb9a3bbd95f4d5c4aef2d84/images/bcam1_layout.png)

## 4-bit BCAM Array
### Xschem
![image](https://github.com/joez-7/BCAM-Array-SKY130/blob/2de8018213b4eca66d855cd2445a9a2529ffa4bb/images/bcam_row4.png)

### Layout
![image](https://github.com/joez-7/BCAM-Array-SKY130/blob/a957816dd77f1167cfb9a3bbd95f4d5c4aef2d84/images/bcam_row4_layout.png)

## References
1. K. Pagiamtzis and A. Sheikholeslami, *Content-Addressable Memory (CAM) Circuits and Architectures: A Tutorial and Survey*, *IEEE Journal of Solid-State Circuits*, vol. 41, no. 3, pp. 712–727, Mar. 2006. [DOI](https://doi.org/10.1109/JSSC.2005.864128)
2. N. H. E. Weste and D. Money Harris, CMOS VLSI Design: A Circuits and Systems Perspective, 4th ed. Boston, MA, USA: Addison-Wesley/Pearson, 2010. ISBN: 978-0-321-54774-3.
