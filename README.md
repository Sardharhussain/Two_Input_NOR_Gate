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
  * [Symbol](#symbol)
* [Test Bench](#test-bench)
  * [Test Bench Schematic](#test-bench-schematic) 
  * [Params set for input voltage source A](#params-set-for-input-voltage-source-A)
  * [Params set for input voltage source B](#Params-set-for-input-voltage-source-B)
  * [Model files inclusion](#Model-files-inclusion)
  * [Transient Settings](#transient-settings)
  * [waveform](#waveform)
  * [Netlist](#netlist)
  * [Primewave Definition](#primewave-definition)
  * [Primewave Log File](#primewave-log-file)
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
