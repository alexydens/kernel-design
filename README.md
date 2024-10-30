# Txapela
## Directories
### `fs`:
File system.
- `inode.h`:        Inode structure.
- `ext2.h`:         Ext2 file system driver.
### `io`:
Input/Output drivers.
- `port.h`:         Port I/O.
- `tty.h`:          A simple terminal interface, drawn to the provided buffer.
### `mem`:
Memory management.
- `pfa.h`:          Page frame allocator.
- `vmm.h`:          Virtual memory manager.
- `kheap.h`:        Kernel heap allocator.
### `ext`:
External code (not written for this project, likely not by members of it).
### `core`:
Code used almost everywhere.
- `types.h`:        Basic types: `u<8-64>`, `i<8-64>`, `f<32-64>`, `bool`, `size_t`.
- `consts.h`:       Type min/max, `NULL`, `PAGE_SIZE`, context, etc.
- `utils.h`:        Utility macros and functions.
- `logging.h`:      Logging functionality.
### `arch`:
Architecture-specific code.
- `segmentation.h`: Set up segmentation.
- `interrupts.h`:   Set up interrupts.
- `timer.h`:        Set up timer.
- `paging.h`:       Set up paging.
- `memmap.h`:       Get a memory map of RAM.
## Logging
### Log levels
- Success:      `[SUCCESS     ]: Message.`.
- Initializing: `[INITIALIZING]: Message.`.
- Info:         `[INFO        ]: Message.`.
- Warning:      `[WARNING     ]: Message.`.
- Error:        `[ERROR       ]: Message. Action taken.`.
- Kernel panic: `[KERNEL PANIC]: Message.\r\n<CPU DUMP>`.
### CPU dump format
```
CPU DUMP:
- rax:    0x0000000000000000  - r8:     0x0000000000000000
- rbx:    0x0000000000000000  - r9:     0x0000000000000000
- rcx:    0x0000000000000000  - r10:    0x0000000000000000
- rdx:    0x0000000000000000  - r11:    0x0000000000000000
- rsi:    0x0000000000000000  - r12:    0x0000000000000000
- rdi:    0x0000000000000000  - r13:    0x0000000000000000
- rbp:    0x0000000000000000  - r14:    0x0000000000000000
- rsp:    0x0000000000000000  - r15:    0x0000000000000000
- rip:    0x0000000000000000  - rflags: 0x0000000000000000
- cs:     0x0000
- ds:     0x0000
- es:     0x0000              - cr0:    0x0000000000000000
- fs:     0x0000              - cr2:    0x0000000000000000
- gs:     0x0000              - cr3:    0x0000000000000000
- ss:     0x0000              - cr4:    0x0000000000000000
```
### Kernel panic behavior
- Print level message as normal log to TTY (and com1 if possible).
- Print CPU dump to TTY (and com1 if possible).
- Halt indefinitely.
## Header format
```c
/* Include guard */
#ifndef TX_PATH_SYSTEM_H
#define TX_PATH_SYSTEM_H

/* Includes */
/* Includes here... */

/* Consts */
/* Constants relevant to user of system... */
/* Format: #define TX_SYSTEM_MYCONST   value */
/* Use macro consts for enums */

/* Initialize system */
extern bool system_init(void);

/* Any other functions, in a similar fashion */

#endif /* TX_PATH_SYSTEM_H */
```
## Source format
```c
/* Implements path/system.h */
#include <path/system.h>

/* Consts */
/* Consts that don't need to be public */

/* Globals */
/* I guess these are like members, if this was an object - any state */

/* Initialize system */
bool system_init(void) {
  /* Implement... */
  return true;
}

/* Other functions... */
```
