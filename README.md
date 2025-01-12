# SAMSUNG RISC-V

RISC-V Talent Development Program, powered by Samsung Semiconductor India Research (SSIR) along with VLSI System Design (VSD)

## Basic Details
**Name:** Rohit J  
**College:** The National Institute Of Engineering Mysuru <br>
**Email ID:** jrohit0812@gmail.com  
**LinkedIN Profile:** [Rohit](https://www.linkedin.com/in/rohitj264/)


----------------------------------------------------------------------------------------------------------------

<details>
<summary><b>Task 1:</b> Implementation of sum of numbers from 1 to n using both c program and riscv command</summary> 
           <br>                                                                                                                                                   <p>This task showcases a neat program developed in C-language that allows users to calculate the sum of integers at varying scales. The code itself can be executed via GCC syntax where you can generate the output via ./a.out.

In addition, there is another version of the code available which uses RISC-V architecture, however this does implement two of its own optimization strategies which include: -O1 and -Ofast.<br> 
### What is -O1 and -Ofast?
> * -O1: As this strategy encompasses a range of radical transformations and changes…the volume of generated assembly code is quite large.<br> 
> * -Ofast:The strategy shifts its main focus to increased speed around and turns on the more robust performance modifications which would ultimately produce less assembly code.

In order to achieve the best possible performance and assemble code -O1 is your best shot. But, if you wish to complete the task in the shortest span of time possible then Ofast will prove to be valuable.
 </p>
</details>

----------------------------------------------------------------------------------------------------------------

<details>
<summary><b>Task 2:</b> Performing SPIKE Simulation and Debugging the C code with Interactive Debugging Mode using Spike</summary> 

### What is SPIKE in RISCV?
> * A RISC-V ISA is a simulator, enabling the testing and analysis of RISC-V programs without the need for actual hardware.  
> * Spike is a free, open-source C++ simulator for the RISC-V ISA that models a RISC-V core and cache system. It can be used to run programs and a Linux kernel, and can be a starting point for running software on a RISC-V target.  
### What is pk (Proxy Kernel)?  
> * The RISC-V Proxy Kernel, pk , is a lightweight application execution environment that can host statically-linked RISC-V ELF binaries.  
> * A Proxy Kernel in the RISC-V ecosystem simplifies the interaction between complex hardware and the software running on it, making it easier to manage, test, and develop software and hardware projects.

*C program which calculates sum of even numbers from 1 to n*
```
#include <stdio.h>

int main()
{
    int i, sum=0,n=100;
    for(i=2; i<=n; i+=2)
    {
	sum += i;
    }

    printf("Sum of all even number between 1 to %d = %d\n", n, sum);

    return 0;
}

```  
</details>
