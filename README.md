# Two_input_NOR_gate
Design and Analysis of two input NOR gate in 180nm CMOS technology using ESIM compiler™️
## Table of Contents
* [Abstract](#Abstract)
* [Truth Table](#Truth-Table)
* [Tools used](#Tools-used)
* [Reference circuit diagram](#reference-circuit-diagram)
* [Reference circuit waveform](#reference-circuit-waveform)
* [Circuit designing](#circuit-designing)
  * [Schematic](#schematic)
* [KiCad to ngspice](#Kicad-to-ngspice)
  * [kicad to ngspice](#kicad-to-ngspice)
  * [Params set for input voltage source A](#params-set-for-input-voltage-source-A)
  * [Params set for input voltage source B](#Params-set-for-input-voltage-source-B)
  * [Mosfet Models](Mosfet-Models)
  * [Transient Settings](#transient-settings)
  * [waveform](#waveform)
  * [Netlist](#netlist)
* [Conclusion](#conclusion)
* [Acknowledments](#acknowledgements)
* [Author](#author)
* [References](#references)

## Abstract
The aim of the work is to design a NOR gate in 180nm CMOS technology on ESIM IC Design platform. In Digital Electronics, a NOR gate is logic circuit which outputs Logic is high when both the inputs are logic low. Other basic gates such as AND, OR, NOT etc. can be designed Using a NOR gate. As it is the series combination of an NOT gate and OR gate. Due to this reason, it is called a UNIVERSAL gate.
The parallel connection of the two n-channel transistors between GND and the gate-output ensures that the gate-output is driven low (logical 0) when either gate input A or B is high (logical 1). The complementary series-connection of the two transistors between VCC and gate-output means that the gate-output is driven high (logical 1) when both gate inputs are low (logical 0).

## Truth Table
<!-- !(https://user-images.githubusercontent.com/100688517/157283736-a26314fb-7e80-412e-9e76-d5ae16c0047e.jpeg)-->
<img src="https://user-images.githubusercontent.com/100688517/157283736-a26314fb-7e80-412e-9e76-d5ae16c0047e.jpeg" width="550" height="450">

## Tools used
* ESIM IC Design Platform.

## Reference circuit diagram
<!-- ![reference circuit diagram](https://user-images.githubusercontent.com/100688517/157284841-081af758-78c9-48f3-8cec-cfd587f802d3.png)-->
![image](https://user-images.githubusercontent.com/100688517/157284841-081af758-78c9-48f3-8cec-cfd587f802d3.png)

## Reference circuit waveform
<!-- ![Reference circuit waveform](https://user-images.githubusercontent.com/100688517/157285413-7bacbab8-cf8c-4d02-8e8a-988ecac96cf2.png)-->
![image](https://user-images.githubusercontent.com/100688517/157285413-7bacbab8-cf8c-4d02-8e8a-988ecac96cf2.png)

## Circuit Designing
* **Schematic Diagram** 
   - Before we create a schematic of the circuit, We should create a project to creat schematic of the required circuit.
   - Next open schematic tab, In schematic add the required parameters which are presented in the parameters tab.
   - Now connect the all parameters with the wires. After creation of the schematic generate the Netlist by  clocking on the netlist feature which is      presented in the schematic tab.

![Schematic](https://user-images.githubusercontent.com/100688517/157289535-f4b584b7-a519-47d7-9cb4-30ae70585312.png)

## KiCad to ngspice
* **KiCad to ngspice**
   - Now that we have design a schematic of the circuit. Now we need to convert it into ngspice from Kicad.
   - In Kicad to ngspice conversation we need to give the values of Input A,B voltage source and mosfet models.
   - You can see below the voltage, rise time, fall time, pulse width and time period of the clock pulse applied to one of the inputs.
 
### Params set for input voltage source A
![Input_A_Parameters](https://user-images.githubusercontent.com/100688517/157291473-285bff0b-cb1c-4bd8-a745-98726977072e.png)

   - You can see below the voltage, rise time, fall time, pulse width and time period of the clock pulse applied to one of the inputs.

### Params set for input voltage source B
![Input_B_Parameters](https://user-images.githubusercontent.com/100688517/157291813-20d6bf9f-c42b-4b4c-bfd5-4923dbb3b823.png)

* **Mosfet Models**
   - You can see below the N Mosfet model parameters.

![NMOS_Parameters](https://user-images.githubusercontent.com/100688517/157292730-e2ba6a62-e268-40aa-a681-a81d3752bc63.png)

- You can see below the P Mosfet model Parameters.

![PMOS_Parameters](https://user-images.githubusercontent.com/100688517/157292882-4e159f6f-e494-4b58-b93d-d4dd2b2d6d5c.png)

* **Transient Settings**
    - In Kicad to ngspice conversation only we need to give the transition time.
   
![Transient_Analysis](https://user-images.githubusercontent.com/100688517/157293344-7869d4aa-60d2-49eb-9068-b685c8223457.png)

* **waveform**
    - we need to go to _'Simulation and Run Simulation to generate output of the circuit.
    - So the waveform with the input values will be created and netlist will be generated.
    - Here Green colour wave indicates input A i.e,V(a),Red colour wave indicates input B i.e,V(b) and blue indicates V(out)

![Waveforms](https://user-images.githubusercontent.com/100688517/157294063-0be847d8-3492-42a3-b8cb-44179e66f82a.png)

* **Netlist**
    - The netlist cir.out is generated at our local path at where we created project.
    - You can see below.

```
* d:\esim\nor_gate\nor_gate.cir
.include NMOS-180nm.lib
.include PMOS-180nm.lib
m2 net-_m2-pad1_ a net-_m2-pad3_ net-_m2-pad3_ CMOSP
m3 vout b net-_m2-pad1_ net-_m2-pad1_ CMOSP
v1 net-_m2-pad3_ gnd  dc 5
v2  b gnd pulse(0 3.3 1u 0.1n 0.1n 4u 8u)
v3  a gnd pulse(0 3.3 1u 0.1n 0.1n 2u 4u)
* u1  a plot_v1
* u2  b plot_v1
m1 vout a net-_m1-pad3_ net-_m1-pad3_ CMOSN
m4 vout b net-_m1-pad3_ net-_m1-pad3_ CMOSN
* u3  vout plot_v1
.tran 0.1e-7 20e-06 0e-00
* Control Statements
.control
run
print allv > plot_data_v.txt
print alli > plot_data_i.txt
plot v(a)
plot v(b)
plot v(vout)
.endc
.end

```
## Conclusion
Thus, the two input NOR gate is being designed and simulated with the 180nm CMOS technology using ESIM compiler with 4 MOSFETs.

## Acknowledgements

* FOSSEE TEAM,IIT BOMBAY.
* Mr.[Kunal Ghosh](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836) Co-Founder at VLSI System Design(VSD).
* Sumanto Kaur,eSim Team,FOSSEE.
* Madhuri Kada,eSim Team,FOSSEE.
* [Mixed signal circuit design Hackathon using eSim](https://hackathon.fossee.in/esim/)

## Author
 * Sardhar Hussain Shaik, Bachelor of Technology in Electronics and Communication Engineering, Ellenki College of Engineering and Technology  Hyderabad-502319.
 
## References
* [CMOS NOR Implementation Technologies](https://www.ques10.com/p/26345/draw-2-input-cmos-nor-gate-and-using-equivalent--1/?)
* [CMOS NOR Implementation Technologies](https://tams.informatik.uni-hamburg.de/applets/hades/webdemos/05-switched/40-cmos/nor.html)
