# puce6502

This is a simple and readable emulation of the MOS 6502 CPU\
It passes the [Klaus Test Suite](https://github.com/Klaus2m5/6502_65C02_functional_tests)\
It implements all original instruction and is cycle accurate excepted for :

*Absolute-X, absolute-Y, and Zero page-Y addressing modes which need an extra cycle if indexing crosses a page boundary, or if the instruction writes to memory.*

You can easely interface it with your code using the provided two functions :

```
void puce6502Reset();
void puce6502Exec(long long int cycleCount);
```

RAM and ROM are implemented using 8 bits integer arrays. And are directly accessible to you code to load ROM binary images or optimise video generation\
RAM starts at adress 0x000\
Update this three #define to adapt it to your needs :
```
#define ROMSTART 0xD000
#define ROMSIZE  0x3000
#define RAMSIZE  0xC000
```

you are expected to provide a function to handle read and writes to locations not
in ROM or in RAM (for Soft Switches, extension cards ROMs, PIA, VIA, ACIA etc...)

```
extern uint8_t softSwitches(uint16_t address, uint8_t value);
```

For examples of use, you can refer to [reinette II plus](https://github.com/ArthurFerreira2/reinette-II-plus) a french Apple II plus emulator.

Have fun !
