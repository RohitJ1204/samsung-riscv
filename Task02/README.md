## C program which calculates sum of even numbers from 1 to n
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
### Compilation of C-Code using gcc command 
```
gcc sumeven2ton.c
./a.out
```
![C Code compiled on gcc Compiler](https://github.com/RohitJ1204/samsung-riscv/blob/f04d62bffa18712242dd1848c9c17867f664fe6b/Task02/Command_terminal.png)

### RISCV Command
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum_1ton.o sum_1ton.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum_1ton.o sum_1ton.c
```
### *Descriptions of the keyword used in above command*  
* **-mabi=lp64:** This option specifies the ABI (Application Binary Interface) to use ```lp64```, which is for 64-bit integer, long and pointer size. This ABI is used for 64-bit RISCV architecture.  
* **-march=rv64i:** This option specifies the architecture that we use, which is rv64i, indicates the 64-bit RISCV base integer instruction set. This also confirms the targeting of 64-bit architecture.  
* **riscv-objdump:** A tool for disassembling RISC-V binaries, providing insights into the code structure and helping in debugging.  
* **-Ofast:** The option -Ofast in the command ```riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c``` is a compiler optimization flag used with the GNU Compiler Collection (GCC). This flag is used to instruct the compiler to optimize the generated code for maximum speed. The use of ```-Ofast``` is typically chosen for applications where execution speed is critical and where deviations from standard behavior are acceptable. However, it's important to test thoroughly, as this level of optimization can introduce subtle bugs, especially in complex calculations or when strict compliance with external standards is required.  
* **-O1:** This options is an optimization level that tells the compiler to optimize the generated code but without greatly increasing compilation time. -O1 aims to reduce code size and execution time while keeping the compilation process relatively quick.

### Assembly language code obtained for riscv-o1 command
![riscv-O1](https://github.com/RohitJ1204/samsung-riscv/blob/d9f0afde47c7cc3482a0cd4081ae4abddb0726f3/Task02/riscv-O1.png)

### Assembly language code obtained for riscv-ofast command
![riscv-Ofast](https://github.com/RohitJ1204/samsung-riscv/blob/d9f0afde47c7cc3482a0cd4081ae4abddb0726f3/Task02/riscv-Ofast.png)

## Testing the SPIKE Simulator
The target is to run the ```sumeven2ton.c``` code using both ```gcc compiler``` and ```riscv compiler```, and both of the compiler must display the same output on the terminal. So to compile the code using **riscv compiler**, use the following command:  
```
spike pk sumeven2ton.c
spike -d pk sumeven2ton.c
```
### What is SPIKE in RISCV?
> * A RISC-V ISA is a simulator, enabling the testing and analysis of RISC-V programs without the need for actual hardware.  
> * Spike is a free, open-source C++ simulator for the RISC-V ISA that models a RISC-V core and cache system. It can be used to run programs and a Linux kernel, and can be a starting point for running software on a RISC-V target.  
### What is pk (Proxy Kernel)?  
> * The RISC-V Proxy Kernel, pk , is a lightweight application execution environment that can host statically-linked RISC-V ELF binaries.  
> * A Proxy Kernel in the RISC-V ecosystem simplifies the interaction between complex hardware and the software running on it, making it easier to manage, test, and develop software and hardware projects.
### *Descriptions of the above command*  
* **spike:** Runs the SPIKE RISC-V simulator. 
* **pk:** Loads the proxy kernel to provide a minimal runtime environment. 
* **sumeven2ton:** The compiled RISC-V binary that calculates the sum of even numbers from 2 to 𝑛
* **-d:** Enables debugging mode in SPIKE. It allows you to inspect the execution, set breakpoints, step through instructions, and view memory/registers.
