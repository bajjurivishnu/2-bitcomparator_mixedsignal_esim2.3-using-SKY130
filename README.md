# 2-bitcomparator_mixedsignal_in esim 2.3 using SKY130
## Contents
- [Abstract](#abstract)
- [Reference Circuit Diagram](#reference-circuit-diagram)
- [Reference Waveform](#reference-waveform)
- [Circuit Details](#circuit-details)
- [Truth Table](#truth-table)
- [Software Used](#software-used)
  * [eSim 2.3](#esim-2.3)
  * [NgSpice](#ngspice)
  * [Makerchip](#makerchip)
- [Circuit Diagram in eSim 2.3](#circuit-diagram-in-esim-2.3)
- [Verilog Code](#verilog-code)
- [Makerchip](#makerchip-1)
- [Makerchip Plots](#makerchip-plots)
- [Netlists](#netlists)
- [NgSpice Plots](#ngspice-plots)
- [Steps to run generate NgVeri Model](#steps-to-run-generate-ngveri-model)
- [Steps to run this project](#steps-to-run-this-project)
- [Acknowlegdements](#acknowlegdements)
- [References](#references)


## Abstract
A magnitude Comparator is a combinational
circuit that compares two binary numbers in order to find
out whether one binary number is equal, less than, or
greater than the other binary number. The Circuit will have two inputs one for A and the other for B and have three output terminals, 
one for A > B condition,
one for A = B condition, and one for A<B condition.
## Reference Circuit Diagram
![reference_circuit](https://user-images.githubusercontent.com/100477948/194505561-c4265b6b-5e34-4aec-8672-9befbf0f42d1.jpg)
## Reference Waveform
![reference_waveform](https://user-images.githubusercontent.com/100477948/194507282-2c0d8732-bdb2-41a6-bb75-87162cc90901.png)
## Circuit Details
In the diagram,a 2-bit magnitude comparator is split into two blocks: digital and analog.
</br>
The digital portion of the circuit is implemented using Verilog.
</br>
For the analog portion, the two 3-input ”OR” gates and one 2-input ”AND” gate are replaced with NMOS and
PMOS transistors, making the circuit mixed-signal.
</br>
The output of the mixed signal 2-bit comparator
circuit may be less than, equal to (ET), or greater than.                  
## Truth Table

| Input A1  | Input A0 | Input B1  | Input B0 | Output A<B | Output A=B | Output A>B |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 0  | 0 | 0  | 0 | 0 | 1  | 0  |
| 0  | 0 | 0  | 1 | 1 | 0  | 0  |
| 0  | 0 | 1  | 0 | 1 | 0  | 0  |
| 0  | 0 | 1  | 1 | 1 | 0  | 0  |
| 0  | 1 | 0  | 0 | 0 | 0  | 1  |
| 0  | 1 | 0  | 1 | 0 | 1  | 0  |
| 0  | 1 | 1  | 0 | 1 | 0  | 0  |
| 0  | 1 | 1  | 1 | 1 | 0  | 0  |
| 1  | 0 | 0  | 0 | 0 | 0  | 1  |
| 1  | 0 | 0  | 1 | 0 | 0  | 1  |
| 1  | 0 | 1  | 0 | 0 | 1  | 0  |
| 1  | 0 | 1  | 1 | 1 | 0  | 0  |
| 1  | 1 | 0  | 0 | 0 | 0  | 1  |
| 1  | 1 | 0  | 1 | 0 | 0  | 1  |
| 1  | 1 | 1  | 0 | 0 | 0  | 1  |
| 1  | 1 | 1  | 0 | 0 | 0  | 1  |
| 1  | 1 | 1  | 1 | 0 | 1  | 0  |
## Software Used
### eSim 2.3
It is an Open Source EDA developed by FOSSEE, IIT Bombay. It is used for electronic circuit simulation. It is made by the combination of two software namely NgSpice and KiCAD.
</br>
For more details refer:
</br>
https://esim.fossee.in/home
### NgSpice
It is an Open Source Software for Spice Simulations. For more details refer:
</br>
http://ngspice.sourceforge.net/docs.html
### Makerchip
It is an Online Web Browser IDE for Verilog/System-verilog/TL-Verilog Simulation. Refer
</br> https://www.makerchip.com/

## Circuit Diagram in eSim
The following is the schematic in eSim:
![mixed_signal_marathoncircuit](https://user-images.githubusercontent.com/100477948/194511170-a0571262-7556-4d2a-a240-75bb049d6cd2.png)






