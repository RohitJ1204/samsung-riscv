## C program which calculates sum of numbers from 1 to 100
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
## Compilation of C-Code using gcc command 
```
gcc sumeven2ton.c
./a.out
```
## RISCV Command
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum_1ton.o sum_1ton.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum_1ton.o sum_1ton.c
```
### What is -O1 and -Ofast?
> * -O1: As this strategy encompasses a range of radical transformations and changes…the volume of generated assembly code is quite large.<br> 
> * -Ofast:The strategy shifts its main focus to increased speed around and turns on the more robust performance modifications which would ultimately produce less assembly code.

## Output snapshots

### *Assembly language code obtained for riscv-o1 command*
![Command_Terminal](https://github.com/RohitJ1204/samsung-riscv/blob/7473be92a5a286029068dc9a2268dd040cf5b8e9/Task01/Command_Terminal.png)

### *Assembly language code obtained for riscv-o1 command*
![riscv-O1](https://github.com/RohitJ1204/samsung-riscv/blob/7473be92a5a286029068dc9a2268dd040cf5b8e9/Task01/riscv-O1.png)

### *Assembly language code obtained for riscv-ofast command*
![riscv-Ofast](https://github.com/RohitJ1204/samsung-riscv/blob/7473be92a5a286029068dc9a2268dd040cf5b8e9/Task01/riscv-Ofast.png)

In order to achieve the best possible performance and assemble code -O1 is your best shot. But, if you wish to complete the task in the shortest span of time possible then Ofast will prove to be valuable.
 
