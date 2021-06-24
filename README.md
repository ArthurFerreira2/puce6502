# puce6502

This is a simple and readable emulation of the MOS 6502 CPU\
It implements all original instructions and is cycle accurate\
It also passes the [Klaus Test Suite](https://github.com/Klaus2m5/6502_65C02_functional_tests) : set `_FUNCTIONNAL_TESTS` to 1 and compile it as a standalone program.

API is as simple as :

```C
uint16_t puce6502Exec(unsigned long long int cycleCount);
void puce6502RST();
void puce6502IRQ();
void puce6502NMI();
```

The first function will execute as many instructions as needed to reach cycleCount clock cycles - it will return the updated value of the Program Counter
the 3 others will simulate a RESET, INTERUPT and NON-MASKABLE INTERUPT.

You are expected to provide the functions to handle read and writes to memory (ROM, RAM, Soft Switches, extension cards, PIA, VIA, ACIA etc...)
They have to comply with these prototypes :

```C
uint8_t readMem(uint16_t address);
void writeMem(uint16_t address, uint8_t value);
```

Finnaly, you can import the variable `ticks` (extern ticks) into your code - it holds the accumulated clock cycles since start.

For an example of use, you can refer to [reinette II plus](https://github.com/ArthurFerreira2/reinette-II-plus) a french Apple II plus emulator.

Have fun !
