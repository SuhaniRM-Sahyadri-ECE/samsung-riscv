## RISC-V Talent Development Program
This program is based on RISC-V talent development program.

## 🚀 About Me
Name:SUHANI R M

College: Sahyadri College of Engineering and Management 

Email ID: suhanirm38@gmail.com / suhani.ec23@sahyadri.edu.in






## 🔗 Links
![linkedin](https://www.linkedin.com/in/suhani-r-m-95055b294?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)

![GitHub](https://github.com/SuhaniRM-Sahyadri-ECE)



## Task01-Development of C Program

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
