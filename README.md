# Modified-Array-Multiplier
This repository will represent the design and implementation of 4 bit modified area efficient  Array Multiplier implemented using Synopsis Custom compiler on 28nm technology

# Table of Contents
- [Abstract](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#abstract)
- [Explanation of circuit](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#explanation-of-circuit)
- [Pseudo NMOS logic](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#pseudo-nmos)
- [Reference circuit](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#reference-circuit)
- [Tools](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#tools)
- [AND gate using pseudo-NMOS logic](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#and-gate-using-pseudo-nmos-logic)
- [OR gate using pseudo-NMOS logic](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#or-gate-using-pseudo-nmos-logic)
- [XOR gate using pseudo-NMOS logic](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#xor-gate-using-pseudo-nmos-logic)
- [Half adder module](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#half-adder-module)
- [Full adder module](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#full-adder-module)
- [Array multiplier circuit](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#modified-array-multiplier-1)
- [Transient Analysis](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#transient-analysis)
- [Simulations](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#simulations)
- [Netlist](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#netlist)
- [Acknowledgements](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#acknowledgements)
- [References](https://github.com/keertana372/Modified-Array-Multiplier/edit/main/README.md#references)

# Abstract
Multipliers are widely used for various application like signal processing. Multipliers are used for multiplication of two binary input data. There are different kinds of multipliers with their own advantages and disadvantages. We implemented an array multiplier in this work that has significantly more speed and consumes less area. It is designed using pseudo NMOS logic and the number of transistors is reduced from 2N to N+1, resulting in a smaller area.

# Explanation of circuit
An array multiplier is a digital combinational circuit used for multiplying two binary numbers by employing an array of full adders and half adders. This array is used for the nearly simultaneous addition of the various product terms involved. To form the various product terms, an array of AND gates is used before the Adder array. The multiplier circuit is based on the add shift algorithm. 

# Construction and Working of a 4×4 Array Multiplier
The design structure of the array Multiplier is regular, it is based on the add shift algorithm principle.
                 Partial product = the multiplicand * multiplier bit
where AND gates are used for the product, the summation is done using Full Adders and Half Adders where the partial product is shifted according to their bit orders. In an n*n array multiplier, n*n AND gates compute the partial products and the addition of partial products can be performed by using n* (n – 2) Full adders and n Half adders. The 4×4 array multiplier shown has 8 inputs and 8 outputs
![image](https://user-images.githubusercontent.com/100711811/156215909-b24cdf26-c928-4c3f-be5c-421ed740851c.png)

# Building Blocks of 4×4 Array Multiplier
A full adder has three input lines and two output lines, where we use this as a basic building block of an array multiplier. The following is the example of a 4×4 array multiplier. The leftmost bit is the LSB bit of partial product.Figure given below is Array block diagram 
![image](https://user-images.githubusercontent.com/100711811/156216151-d5b82ad0-fe62-47bb-9655-dad03814ed63.png)

             Figure given below is array-multiplier-block-diagram
 ![image](https://user-images.githubusercontent.com/100711811/156216742-f4771a7f-ea75-4197-bca9-b5cf5a44a037.png)

The rightmost bit is the MSB bit of partial product. The partial products are now shifted towards the left side on multiplication and they are added to get the final product. This process is repeated until no two partial products exit for addition where X0,X1,X2,X3 and Y0,Y1,Y2,Y3 are Multiplicand and Multiplier, summation of all products are partial products. After multiplication we can observe the Z0 - Z7 are final results.  The result of the sum of the partial product is a product. For a 4×4 Array Multiplier, it needs 16 AND gates, 4 Half Adders(HAs), 8 Full Adders (FAs). Total 12 Adders.

# Advantages of 4×4 Array Multiplier
The advantages of array multiplier are,
•	Minimum complexity
•	Easily scalable
•	Easily pipelined
•	Regular shape, easy to place and route

# Pseudo NMOS Logic 
Pseudo-NMOS logic with transistor count N+1 the pull up network is always as compared to the CMOS there is great reduction in number of transistors. Below is the figure of inverter implemented in pseudo-NMOS. PMOS devices are good pull up resistive loads because they are fast and compact. With a fan-in, it's a pseudo-NMOS gate because each input is connected to only one transistor, the burden on the transistor is reduced prior to the gate.Figure given below is Pseudo NMOS gate.

![image](https://user-images.githubusercontent.com/100711811/156217226-e1aea6f2-feba-4f90-9a05-8110a84ea887.png)

The pseudo-NMOS doesn’t offer any advantage for inverter in terms of area as compared to CMOS because both have same number of transistors but other gates like AND,OR,XOR it offers advantages below is the Table which gives comparison between number of transistors in CMOS and pseudo-NMOS logic, the advantage of reduction area it comes at cost of increased static power consumption because P-MOS is always connected to supply irrespective of input.

# Reference Circuit
![image](https://user-images.githubusercontent.com/100711811/156217359-abb484c9-ce1f-4ea5-8d99-b444c0c6e279.png)

# Tools

•	Synopsys Custom Compiler:  The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

•	Synopsys Primewave:  PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

•	Synopsys 28nm PDK:  The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.

# AND Gate using Pseudo NMOS logic
![image](https://user-images.githubusercontent.com/100711811/156217660-d155305a-61cf-4b2f-b8b3-cacc00951a75.png)

#  OR Gate using Pseudo NMOS logic
![image](https://user-images.githubusercontent.com/100711811/156217714-7fcd2a8c-969f-4a58-8390-fa761e8629e8.png)

# XOR Gate using Pseudo NMOS logic
![image](https://user-images.githubusercontent.com/100711811/156217798-cb6cf662-9dc5-4d22-b54b-7deb48748c11.png)

# Half adder Module
![image](https://user-images.githubusercontent.com/100711811/156217875-7a5c03ff-9ca1-4265-acc4-cf9f228ff930.png)

# Full adder Module
![image](https://user-images.githubusercontent.com/100711811/156217929-5a0ca63f-5f79-49e5-8712-9f64579ffc82.png)

# Modified Array Multiplier
![image](https://user-images.githubusercontent.com/100711811/156217996-a4df4985-9958-4a40-9d62-ed7142c9342a.png)

# Transient Analysis
![image](https://user-images.githubusercontent.com/100711811/156218086-5fb1fabf-cfab-4661-b08d-1be61cd4dd91.png)
![image](https://user-images.githubusercontent.com/100711811/156218154-18566319-e837-4dd4-9a20-14d51a229a24.png)

# Simulations
![image](https://user-images.githubusercontent.com/100711811/156218198-39c15226-6be2-4956-9c03-720709ef0b50.png)

When given input as X=1011 & Y=1101 then the output we get Z=1000111.The array multiplier implemented with pseudoNMOS gives an advantage our CMOS in terms of number of
transistors.The advantage of array multiplier implemented with pseudoNMOS has advantage in reduction of number of transistors. If implemented with CMOS number of transistors would be 260 and when implemented with Pseudo-NMOS number of transistors are176 and therefore there is reduction in number of area. 

# Netlist 
Refer to the netlist of the circuits here:[Netlist.txt](https://github.com/keertana372/Modified-Array-Multiplier/files/8163608/Netlist.txt)

# Author
Sirigibattula Keertana, MTech VLSI Design, Vellore Institute of Technology, Vellore.

# Acknowledgements
-	Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd.
-	Cloud Based Analog IC Design Hackathon
-	Synopsys India
-	Chinmay panda, IIT Hyderabad

# References
[1] M. C. Park, B. W. Lee, G. M. Kim and D. H. Kim, "Compact and fast multiplier using dual array tree structure," 1993 IEEE International Symposium on Circuits and Systems, 1993, pp. 1817- 1820 vol.3, doi: 10.1109/ISCAS.1993.394099.

[2] N. Subba, A. Salman, S. Mitra, D. E. Ioannou and C. Tretz, "Pseudo-nMOS revisited: impact of SOI on low power, high speed circuit design," 2000 IEEE International SOI Conference. Proceedings (Cat. No.00CH37125), 2000, pp. 26-27, doi: 10.1109/SOI.2000.892752.

[3] https://en.wikipedia.org/wiki/Binary_multiplier

[4] Khushbu Maheshwari, Prof. Mukesh Tiwari "Design and Implementation of 4-bit Array Multiplier for Low Power in 45nm CMOS Technology" International Journal of Engineering Research & Technology (IJERT) IJERT ,ISSN: 2278-0181, Vol. 3 Issue 4, April - 2014.

















     

