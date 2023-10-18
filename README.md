###  RISC-V Repo

# Table of contents

<a name="top"></a>

<details>
<summary>DAY-3 : Digital Logic with TL-Verilog in Makerchip IDE</summary>
<br>

#### Task-1 : Logic Gates

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/24cfbcd8-3ff2-4cae-b4fa-488e5c77af5c)

#### Task-2 : Lab - Makerchip platfrom
To use Makerchip IDE, you need to visit makerchip website at [http://makerchip.com/](http://makerchip.com/) and launch Makerchip IDE
To access a specific example, please follow these steps:
1) **Navigate to the 'Learn' section**
2) **Click on 'Examples'**
3) **Load 'FGPA Multiplier' Example**

![WhatsApp Image 2023-10-18 at 9 43 54 AM](https://github.com/vaishbv/RISC-V/assets/79531808/8145d97c-80af-4627-a3c5-55b2a9acddb2)




#### Task-3 : Lab - Combinational logic
**A) Inverter**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes(On line 16,in place of `//...` type `$out = ! $in;`)**
4) **Compile(Ctrl+E)**

![WhatsApp Image 2023-10-18 at 10 25 36 AM](https://github.com/vaishbv/RISC-V/assets/79531808/5eeeb790-06be-475a-94a5-b81be24e0563)


**B) XOR Gate**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
$out = ! $in;
$out1 = ($in1 ^ $in2);
```
4) **Compile(Ctrl+E)**
![WhatsApp Image 2023-10-18 at 10 27 17 AM](https://github.com/vaishbv/RISC-V/assets/79531808/74f4fb78-0a79-4d8f-b68f-48a09c7378a8)


**C) Vectors**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
$out[4:0] = $in1[3:0] + $in2[3:0];
```
4) **Compile(Ctrl+E)**
![WhatsApp Image 2023-10-18 at 10 28 12 AM](https://github.com/vaishbv/RISC-V/assets/79531808/28738228-7bd5-4dd2-9a1a-bfa889614c90)


**D) Mux without vector & with vectors**
1) **Click on 'Examples'**
2) **Load Default Template**
   
3a) **Go to editor and make changes**
```
$out = $sel ? $in1 : $in2;
```
4a) **Compile(Ctrl+E)**
![WhatsApp Image 2023-10-18 at 10 31 42 AM](https://github.com/vaishbv/RISC-V/assets/79531808/d020813f-048b-4d41-90df-0c49ab5fa199)


3b) **Go to editor and make changes**
```
$out[7:0] = $sel ? $in1[7:0] : $in2[7:0];
```
4b) **Compile(Ctrl+E)**
![1](https://github.com/vaishbv/RISC-V/assets/79531808/9ff88952-dbd2-4a16-a34a-0bdadbfa86f9)



**E) Simple Calculator**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
$val1[31:0] = $rand1[3:0]; 
$val2[31:0] = $rand2[3:0];
$sum[31:0] = $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$qut[31:0] = $val1 / $val2;
$out[31:0] = $op[1] ? ($op[0] ? $qut: $prod): ($op [0] ? $diff: $sum);
```
4) **Compile(Ctrl+E)**
![2](https://github.com/vaishbv/RISC-V/assets/79531808/06c3893e-3e40-4ff0-9962-9daa830e73d1)



#### Task-4 : Sequential logic 

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/0d548af2-e42f-48fd-9a33-fe47df3775fb)

**A) Fibonacci series**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
$fib[31:0] = $reset ? 1 : (>>1$fib + >>2$fib); 
```
4) **Compile(Ctrl+E)**
![WhatsApp Image 2023-10-18 at 10 47 12 AM](https://github.com/vaishbv/RISC-V/assets/79531808/285f0634-2036-454b-91a0-4b7988bfceaa)


**B) Up-Counter**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
$num[2:0] = $reset ? 0 : (>>1$num + 1); 
```
4) **Compile(Ctrl+E)**
![3](https://github.com/vaishbv/RISC-V/assets/79531808/e12aac72-dd41-4483-a943-05492e0a5403)



**C) Sequential Calculator**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
$val1[31:0] = (>>1$out); 
$val2[31:0] = $rand2[3:0]; 
$sum[31:0] = $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$qut[31:0] = $val1 / $val2;
$out[31:0] = $op[1] ? ($op[0] ? $qut: $prod): ($op [0] ? $diff: $sum); 
```
4) **Compile(Ctrl+E)**
![4](https://github.com/vaishbv/RISC-V/assets/79531808/5ec5b390-4ca3-47f9-b21f-9ccb7c13432f)



#### Task-5 : Pipelined logic
**A) A simple pipeline through Pythagorean example**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
`include "sqrt32.v"
|calc
      @1
         $aa_sq[31:0] = $aa[3:0] * $aa;
         $bb_sq[31:0] = $bb[3:0] * $bb;
      @2
         $cc_sq[31:0] = $aa_sq + $bb_sq;
      @3
         $cc[31:0] = sqrt($cc_sq);
```
4) **Compile(Ctrl+E)**
![5](https://github.com/vaishbv/RISC-V/assets/79531808/4daa2704-aaa6-4e4b-af60-8c9e638b3684)



**B) Pipeline Implementation**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
|comp
      @1
         $err1 = $bad_input || $illegal_op;
      @2
         $err2 = $err1 || $over_flow;
      @3
         $err3 = $div_by_zero || $err2;
```
4) **Compile(Ctrl+E)**
![6](https://github.com/vaishbv/RISC-V/assets/79531808/3820f592-0a5e-40c2-8322-5b5b1292d808)




#### Task-6 : Validity
+ Easier debug
+ Cleaner design
+ Better error checking
+ Automated clock gating

**A) 2 cycle calculator with validity**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
|calc
      @0
         $reset = *reset;
         
      @1
         $val1 [31:0] = >>2$out [31:0];
         $val2 [31:0] = $rand2[3:0];
         
         $valid = $reset ? 1'b0 : >>1$valid + 1'b1;
         $valid_or_reset = $valid || $reset;
         
      ?$valid_or_reset
      @1
         $sum [31:0] = $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $qut [31:0] = $val1 / $val2;
         
      @2
         $out [31:0] = $reset ? 32'b0 :
                      ($op[1:0] == 2'b00) ? $sum :
                      ($op[1:0] == 2'b01) ? $diff :
                      ($op[1:0] == 2'b10) ? $prod :
                                              $qut ;
```
4) **Compile(Ctrl+E)**
![7](https://github.com/vaishbv/RISC-V/assets/79531808/149ddf9d-0711-40b7-9365-de028b4e6fb2)



**B) Distance Calculator**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
|calc
      @1
         $reset = *reset;
         
      ?$valid
         @1
            $aa_sq[31:0] = $aa[3:0] * $aa;
            $bb_sq[31:0] = $bb[3:0] * $bb;;
         @2
            $cc_sq[31:0] = $aa_sq + $bb_sq;;
         @3
            $cc[31:0] = sqrt($cc_sq);
      @4
         $total_distance[63:0] =
            $reset ? 0 :
            $valid ? >>1$total_distance + $cc :
                     >>1$total_distance;
```
4) **Compile(Ctrl+E)**
![8](https://github.com/vaishbv/RISC-V/assets/79531808/0a35abf0-1404-48f1-9aed-4f98148191cd)




**A) Calulator Memory**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
|calc
      @0
         $reset = *reset;
         
      @1
         $val1 [31:0] = >>2$out [31:0];
         $val2 [31:0] = $rand2[3:0];
         
         $valid = $reset ? 1'b0 : >>1$valid + 1'b1;
         $valid_or_reset = $valid || $reset;
         
      ?$valid_or_reset
      @1
         $sum [31:0] = $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $qut [31:0] = $val1 / $val2;
         
      @2
         $mem[31:0] = $reset ? 32'b0 :
                      ($op[2:0] == 3'b101) ? $val1 : >>2$mem ;
         
         $out [31:0] = $reset ? 32'b0 :
                      ($op[2:0] == 3'b000) ? $sum :
                      ($op[2:0] == 3'b001) ? $diff :
                      ($op[2:0] == 3'b010) ? $prod :
                      ($op[2:0] == 3'b011) ? $qut  :
                      ($op[2:0] == 3'b100) ? >>2$mem : >>2$out ;
```
4) **Compile(Ctrl+E)**
![9](https://github.com/vaishbv/RISC-V/assets/79531808/da38255c-23dc-492d-abd2-c0335f9d56bd)



[Back to Top](#top)

</details>

<details>
<summary>DAY 4 : Basic RISC-V CPU Micro Architecture</summary>
<br>

# RISC-V Architecture Block Diagram

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/1695d5f6-eab9-4279-9419-b2817800b002)

## Overview
This RISC-V Architecture Block Diagram illustrates the fundamental components and their interactions within a computer system based on the RISC-V instruction set architecture. RISC-V is a modular and customizable architecture, providing a versatile framework for designing processors tailored to specific application requirements.

## Components
1. **CPU (Central Processing Unit)**
   - *Description*: The CPU serves as the core of the RISC-V processor, responsible for executing instructions. It includes multiple stages:
     - Instruction Fetch (IF): Fetches instructions from memory.
     - Instruction Decode (ID): Decodes the fetched instructions.
     - Execution (EX): Performs arithmetic and logic operations.
     - Memory (MEM): Manages data memory access.
     - Write Back (WB): Writes results back to registers.

2. **Instruction Memory**
   - *Description*: This memory component stores the program's instructions that the CPU fetches and executes. It's essential for the program's proper execution.

3. **Data Memory**
   - *Description*: Data Memory stores data used by the CPU during program execution. It is crucial for data manipulation and storage.

4. **Registers**
   - *Description*: Registers are a set of general-purpose storage units used for temporary data storage and manipulation by the CPU. They play a pivotal role in instruction execution.

5. **Control Unit**
   - *Description*: The Control Unit manages control signals and coordinates the activities of the CPU's components, ensuring the proper execution of instructions.

6. **ALU (Arithmetic Logic Unit)**
   - *Description*: The ALU performs arithmetic and logic operations as directed by the CPU's instructions. It is the computational workhorse of the processor.

7. **Instruction Decoder**
   - *Description*: The Instruction Decoder interprets and decodes instructions fetched from memory. It translates instructions into actions for the CPU to execute.

8. **Cache Memory**
   - *Description*: Cache Memory provides fast access to frequently used instructions and data. It helps improve the system's overall performance by reducing memory access times.

9. **Bus Interface**
   - *Description*: The Bus Interface facilitates data transfer between the CPU, memory, and peripherals. It ensures efficient communication within the system.

10. **Peripherals**
    - *Description*: Peripherals are external devices such as input/output controllers, timers, and more. They connect to the CPU, enhancing the system's functionality by allowing interaction with the outside world.

For the consecutive labs, we will use the "RISC-V lab starting point code" from https://github.com/stevehoover/RISC-V_MYTH_Workshop.

Use the following links : [Link for the starter code](https://myth.makerchip.com/sandbox?code_url=https:%2F%2Fraw.githubusercontent.com%2Fstevehoover%2FRISC-V_MYTH_Workshop%2Fmaster%2Frisc-v_shell.tlv#)

All the code files are located within the "DAY4" folder : [Link to DAY4 ](https://github.com/Pavan2280/RISC-V/tree/main/DAY4)

#### Task-1 : Program Counter
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/ee23ca5b-0eaf-43a5-94ee-e992caa385c3)

#### Task-2 : Instruction Fetch
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/7a013f50-0de4-4e51-99ae-61950c45ec13)

#### Task-3 : Instruction Decode
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/7b8a3ee1-d2e8-4cb3-8d73-ea98311150f1)

#### Task-4 : Instruction Decode with validity
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/446d2df0-9793-4b2f-9654-38bbabeac788)

#### Task-5 : Individual Instruction decode
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/02822525-10bf-497d-87af-2306d47ef9a9)

#### Task-6 : Register File Read
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/c6946fc3-2dc0-40b7-adf0-40c1ba37289d)

#### Task-7 : ALU
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/d4402cd0-9ff7-4071-a0f6-b8a71bccb501)

#### Task-8 : Register File Write
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/45f8fea1-7db9-4ede-9c1d-d082f03764cc)

#### Task-9 : Branch Instructions
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/1ec20ce2-3dcf-4a1d-8941-48f3ea3ebaac)

#### Task-10 : Testbench to check functionality
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/e00a3113-f18e-453d-9820-d4327fdf1bd0)

[Back to Top](#top)

</details>

<details>
<summary>DAY 5 : Complete Pipelined RISC-V Micro Architecture </summary>
<br>

[Back to Top](#top)

</details>
