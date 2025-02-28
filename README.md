## RISC-V Talent Development Program
This program is based on RISC-V talent development program.

## 🚀 About Me
Name:SUHANI R M

College: Sahyadri College of Engineering and Management 

Email ID: suhanirm38@gmail.com / suhani.ec23@sahyadri.edu.in

Github ID: ![GitHub](https://github.com/SuhaniRM-Sahyadri-ECE)






<details>
  <summary>Task01 - Development of C program</summary>


## Step01: Fire up the terminal
vsduser@vsduser-VirtualBox:~$
## Step02: Change the directory to home
cd
## Step03: Open leafpad
leafpad sum1ton.c &
## Step04: Write the code
#include<stdio.h>

int main(){

    int sum = 0, n = 100, i;
    for(i=0; i<=n; i++){
        sum+=i;
        printf("The sum from 1 to 100: %d \n", sum);
    }
    return 0;
}
## Step05:  Save the file and run the following prompt in terminal to compile the program
gcc sum1ton.c
## Step06: Run the program
./a.out

![]()
## Step07:  Compile the program in Assembly
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i-o sum1ton.o sum1ton.c


## Step08: Disassemble the sum1ton.o object file for the RISC-V 64-bit architecture, displaying its assembly instructions
riscv64-unknown-elf-objdump -d sum1ton.o
## Step09: Disassemble the sum1ton.o object file for the RISC-V 64-bit architecture, enable easy scrolling and searching for the main
riscv64-unknown-elf-objdump -d sum1ton.o | less

![search for main](https://github.com/SuhaniRM-Sahyadri-ECE/samsung-riscv/blob/main/Task1/task1(main%20search).png?raw=true)

## Step10:  Observe the begining and final bit and count the number of instructions executed using a programmable calculator and verify with the code
![calculation](https://github.com/SuhaniRM-Sahyadri-ECE/samsung-riscv/blob/main/Task1/task1(O1)..png?raw=true)

## Step 11: Compare the results with optimizations (-Ofast)
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv6 4i-o sum1ton.o sum1ton.c


# Once you have the optimized object file, disassemble it again:
riscv64-unknown-elf-objdump -d sum1ton.o | less
![Ofast calculation](https://github.com/SuhaniRM-Sahyadri-ECE/samsung-riscv/blob/main/Task1/task1(Ofast).png?raw=true)

Then, perform the same search for main and instruction count calculations to compare with the non-optimized version.

</details>
<details>
  <summary>Task02 - Simulation with Spike</summary>
  <hr>
## Task02 - Simulation with Spike
*** SPIKE is a simulator for the RISC-V architecture, allowing you to test and debug RISC-V programs without needing real hardware. It simulates a RISC-V processor and cache, and can run programs or even a Linux kernel.
PK (Proxy Kernel) is a lightweight environment that helps run statically-linked RISC-V programs, acting like a simple operating system.

Test SPIKE through running a sample program (e.g. sum1ton.c) using both the gcc compiler and the RISC-V compiler. Confirm the two compilers produced the same output in executing the program on the simulator.
## Step01: Compile and run the program
cat sum1ton.c

gcc sum1ton.c

./a.out
![compile](https://github.com/SuhaniRM-Sahyadri-ECE/samsung-riscv/blob/main/Task2/spike%20run%20the%20debugger.png.png?raw=true)
## Step02: Compile with Optimization Level -O1
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
## Step03: Generate an Object Dump
riscv64-unknown-elf-objdump -d sum1ton.o | less
## Step04: Run the Program with the SPIKE Debugger
spike -d pk sum1ton.o
## Step05: Compile with Optimization Level -Ofast
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
riscv64-unknown-elf-objdump -d sum1ton.o | less
## Step06: Run the Program with the SPIKE Debugger
spike -d pk sum1ton.o
## Step07: Compare Outputs
O1 debug using Spike
![O1](https://github.com/SuhaniRM-Sahyadri-ECE/samsung-riscv/blob/main/Task2/spike%20O1%20debugger.png.png?raw=true)
## Ofast debug using Spike
![Ofast](https://github.com/SuhaniRM-Sahyadri-ECE/samsung-riscv/blob/main/Task2/spike%20Ofast%20debugger.png.png?raw=true)
Compare Outputs Once both versions (-O1 and -Ofast) have been compiled and run, compare the outputs from both compilers. You should check:

Whether the outputs match between the GCC and RISC-V compiler. Any differences in the assembly code or execution behavior due to optimization.

</details>

<details>
  <summary> Task 03 </summary>
    
## ## 15 Unique RISC-V Instructions and their 32- Bit encodings: 
 ##RISC-V instructions and their Encodings:

1) add a0, a0, a1

   Type: R-type

   Binary Encoding: 0000000 00101 00100 000 00100 0110011


2) li a0, 0x0

   Type:Pseudo -> I-type

   Binary Encoding:0000000 00000 00000 000 00100 0010011

3) lui a5, 0xfffff

   Type:U-type

   Binary Encoding:1111111 111111 11111 00000 10101 0110111

4) jal ra, 0x44

   Type:J-type

   Binary Encoding:0000000 00100 00100 00000 00001 1101111

5) add sp, sp, 16

   Type:I-type

   Binary Encoding:0000000 10000 00010 000 00010 0010011

6) sub a2, a0, a2

   Type:R-type

   Binary Encoding:0100000 00010 00100 000 00101 0110011

7) lbu a5, 0x1944

   Type:I-type

   Binary Encoding:0000000 10000 01000 100 00101 0000011

8) bnez a5, <label>

   Type:B-type

   Binary Encoding:0000000 10001 01000 001 01000 1100011

9) ret

   Type:I-type (JALR x0)`

   Binary Encoding:0000000 00000 00100 000 00000 1100111

10) auipc a0, 272

    Type:U-type

    Binary Encoding:0000000 01111 11111 000 00000 0010111

11) jalr ra, <main>

    Type:I-type

    Binary Encoding:0001 0000 0000 00001 000 00001 1100111

12) auipc gp, 0x13

    Type:U-type

    Binary Encoding:0000000 00001 00110 000 00110 0010111

13) addi gp, gp, 1780

    Type:I-type

    Binary Encoding:0000000 01101 00110 000 00110 0010011

14) jal ra, <atexit>

    Type:J-type

    Binary Encoding:0000000 00010 01100 00000 00001 1101111

15) lw a0, 0(sp)

    Type:I-type

    Binary Encoding:0000000 00000 00010 010 00100 0000011
   

</details>
<details>
<summary>Task04</summary>
  
  ### 1. **Create a Directory**:
  ### 2. **Create the verilog files using touch command**
  ### 3. **locate the files created and paste the code from the <a href="https://github.com/vinayrayapati/rv32i/blob/main/?> repo </a>**
  Get the Verilog netlist from <a href="https://github.com/vinayrayapati/rv32i/blob/main/iiitb_rv32i.v">RISC-V Core Verilog Netlist.</a>
  Get the testbench from <a href="https://github.com/vinayrayapati/rv32i/blob/main/iiitb_rv32i_tb.v">Testbench for RISC-V Core.
  ### 4. **Compile the Files**
  ### 5. **run the files**
  ### 6. **Open the Waveform File in GTKWave**
  ### 7. **Add Signals to GTKWave:**
  ### 7. **Add Signals to GTKWave:**
  
</details>

<details>
  <summary>Task05: Project Overview</summary>
    
## Ultrasonic Distance Measurement with Alarm


This circuit is designed to measure distance using an ultrasonic sensor (HC-SR04) and trigger a buzzer alarm when an object is detected within a certain range.


## Features

- **Ultrasonic Sensor:** Uses an HC-SR04 ultrasonic sensor to measure the distance to an object.
- **Riscv Board:** Used to control ultrasonic sensor.
- **Buzzer Alarm:** A buzzer alarm sounds when the detected object is too close.
- **Led lights:** Led lights are used to indicate different distances.
  
### Working

The HC-SR04 sensor sends an ultrasonic pulse through the Trig pin.
The pulse reflects off an object and returns to the sensor.
The Echo pin measures the time taken for the pulse to return.
The microcontroller calculates the distance based on the pulse duration.
If the distance is below a threshold, the buzzer is activated.
If the distance is within 10cm then red led turns ON, if the distance exceeds more than 10cm then green led turns ON

### Components Required
  <ul>
  <li>A RISC-V development board (e.g., SiFive, GOWIN FPGA, or similar)</li>
  <li> Ultrasonic Sensor </li>
  <li> Buzzer </li>
  <li> Connecting Wires </li>
  <li> Led </li>
</ul>
<br>

## Circuit Diagram

![](https://github.com/SuhaniRM-Sahyadri-ECE/samsung-riscv/blob/main/Task5/Distance%20measurer%20using%20riscv%20board.jpg)



## Connection Pins
HC-SR04 Ultrasonic Sensor to Microcontroller:

VCC → 5V

Trig → Digital Pin (e.g., PC0)

Echo → Digital Pin (e.g., PC1)

GND → GND

Buzzer to Microcontroller:

Positive (VCC) → Digital Pin (e.g., PC4)

Negative (GND) → GND





    


  
  
