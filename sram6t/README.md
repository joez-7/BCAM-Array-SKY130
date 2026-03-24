# Static Random Access Memory (SRAM 6T)
The SRAM cell is a standard 6-transistor bit-cell created using two cross-coupled CMOS inverters and two NMOS access transistors. The cross-coupled inverters store the data on internal nodes Q and QB, while the access transistors connect the cell to the bitlines when the wordline is asserted. 

When the wordline is low, the access transistors are off, so the cell becomes isolated from the bitlines, and the cross-coupled inverters retain the stored value. During a write operation, the wordline is asserted, allowing access to the cell. Then, the driven bitlines will force one internal node high and the other low. During a read, the wordline is also asserted, but this time the stored data causes a small voltage difference to develop between the two bitlines.

## Schematic
![image](https://github.com/joez-7/BCAM-Array-SKY130/blob/5ba66deec1cfcc1e5e88b3710e10d63e335bc066/images/sram6t.png)

## Layout
![image](https://github.com/joez-7/BCAM-Cell-SKY130/blob/80be3fa1df80c246b9edb976914eac8dde80d5a3/images/sram6t_layout.png)

## References
1. Justin London, *Design and Simulation of 6T SRAM Array*, arXiv:2508.09419 [eess.SY], v1, submitted Aug. 13, 2025. [DOI](https://doi.org/10.48550/arXiv.2508.09419) · [HTML](https://arxiv.org/html/2508.09419v1) 
