# 2-bitcomparator_mixedsignal_esim_SKY130
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
- [Author](#author)
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
In the diagram, a 2-bit magnitude comparator is split into two blocks: digital and analog.
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
## Verilog Code
![verilogcode](https://user-images.githubusercontent.com/100477948/194511593-2f2b4bcb-7eb9-4009-9246-2fec7b5f75d9.png)
## Makerchip
```
\TLV_version 1d: tl-x.org
\SV
/* verilator lint_off UNUSED*/  /* verilator lint_off DECLFILENAME*/  /* verilator lint_off BLKSEQ*/  /* verilator lint_off WIDTH*/  /* verilator lint_off SELRANGE*/  /* verilator lint_off PINCONNECTEMPTY*/  /* verilator lint_off DEFPARAM*/  /* verilator lint_off IMPLICIT*/  /* verilator lint_off COMBDLY*/  /* verilator lint_off SYNCASYNCNET*/  /* verilator lint_off UNOPTFLAT */  /* verilator lint_off UNSIGNED*/  /* verilator lint_off CASEINCOMPLETE*/  /* verilator lint_off UNDRIVEN*/  /* verilator lint_off VARHIDDEN*/  /* verilator lint_off CASEX*/  /* verilator lint_off CASEOVERLAP*/  /* verilator lint_off PINMISSING*/   /* verilator lint_off BLKANDNBLK*/  /* verilator lint_off MULTIDRIVEN*/ /* verilator lint_off WIDTHCONCAT*/  /* verilator lint_off ASSIGNDLY*/  /* verilator lint_off MODDUP*/  /* verilator lint_off STMTDLY*/  /* verilator lint_off LITENDIAN*/  /* verilator lint_off INITIALDLY*/   

//Your Verilog/System Verilog Code Starts Here:
module vishnu_2bitcomp(A1,A0,B1,B0,t0,t1,t2,t3,t4,t5,t6,t7);
input A1,A0,B1,B0;
output t0,t1,t2,t3,t4,t5,t6,t7;
and g1(t0,~A1,B1);
and g2(t1,~A0,B1,B0);
and g3(t2,~A1,~A0,B0);
xnor g4(t3,A1,B1);
xnor g5(t4,A0,B0);
and g6(t5,A1,~B1);
and g7(t6,A0,~B1,~B0);
and g8(t7,A1,A0,~B0);
endmodule

//Top Module Code Starts here:
	module top(input logic clk, input logic reset, input logic [31:0] cyc_cnt, output logic passed, output logic failed);
		logic  A1;//input
		logic  A0;//input
		logic  B1;//input
		logic  B0;//input
		logic  t0;//output
		logic  t1;//output
		logic  t2;//output
		logic  t3;//output
		logic  t4;//output
		logic  t5;//output
		logic  t6;//output
		logic  t7;//output
//The $random() can be replaced if user wants to assign values
		assign A1 = $random();
		assign A0 = $random();
		assign B1 = $random();
		assign B0 = $random();
		vishnu_2bitcomp vishnu_2bitcomp(.A1(A1), .A0(A0), .B1(B1), .B0(B0), .t0(t0), .t1(t1), .t2(t2), .t3(t3), .t4(t4), .t5(t5), .t6(t6), .t7(t7));
	
\TLV
//Add \TLV here if desired                                     
\SV
endmodule
```
## Makerchip Plots
![makerchip_waveforms](https://user-images.githubusercontent.com/100477948/194516845-2181216b-736c-459d-8f43-f20b92c8ceae.png)
## Netlists
![netslist1](https://user-images.githubusercontent.com/100477948/194517868-7251b3ca-5abc-4003-b331-60a67b2daa71.png)
![netlist2](https://user-images.githubusercontent.com/100477948/194518001-8405c5b9-35b7-445c-a26a-b0dc43d4cf51.png)
## NgSpice Plots
![mixed_signal_marathongraph](https://user-images.githubusercontent.com/100477948/194518921-98ad0ba4-de81-4ccf-be08-24ad618b9665.png)
## Steps to run generate NgVeri Model
1. Open eSim
2. Run NgVeri-Makerchip 
3. Add top level verilog file in Makerchip Tab
4. Click on NgVeri tab
5. Add dependency files
6. Click on Run Verilog to NgSpice Converter
7. Debug if any errors
8. Model created successfully
## Author
Vishnu Bajjuri, B.Tech (ECE), Jyothishmathi Institute of Technology and Science, Karimnagar.
## Acknowlegdements
1. FOSSEE, IIT Bombay
2. Steve Hoover, Founder, Redwood EDA
3. Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
4. Sumanto Kar, eSim Team, FOSSEE 
5. https://www.c2s.gov.in/
6. https://www.google.co.in/
7. https://www.vlsisystemdesign.com/
8. https://spoken-tutorial.org/

## References
1. Weste, Neil HE, and David Harris. CMOS VLSI design: a circuits and systems perspective. Pearson Education India, 2015.
2. Mano, M. Morris. Digital logic and computer design. Pearson Education India, 2017
3. https://www.geeksforgeeks.org/magnitude-comparator-in-digital-logic/
