Registers are essentially places where the processor can store memory. You can think of them as buckets in which the processor can store information.

Here is a list of the x64 registers, and what their common use cases are.

    rbp: Base Pointer, points to the bottom of the current stack frame
    rsp: Stack Pointer, points to the top of the current stack frame
    rip: Instruction Pointer, points to the instruction to be executed
    
    General Purpose Registers
    These can be used for a variety of different things.
    rax:
    rbx:
    rcx:
    rdx:
    rsi:
    rdi:
    r8:
    r9:
    r10:
    r11:
    r12:
    r13:
    r14:
    r15:

In x64 linux arguments to a function are passed in via registers. The first few args are passed in by these registers:

    rdi:    First Argument
    rsi:    Second Argument
    rdx:    Third Argument
    rcx:    Fourth Argument
    r8:     Fifth Argument
    r9:     Sixth Argument

There are also different sizes for registers. The typical sizes we will be dealing with are 8 bytes, 4 bytes, 2 bytes, and 1 byte. The reason for these different sizes is due to the advancement of technology, so that we can store more data in a register.

                                +-----------------+---------------+---------------+------------+
                                | 8 Byte Register | Lower 4 Bytes | Lower 2 Bytes | Lower Byte |
                                +-----------------+---------------+---------------+------------+
                                |   rbp           |     ebp       |     bp        |     bpl    |
                                |   rsp           |     esp       |     sp        |     spl    |
                                |   rip           |     eip       |               |            |
                                |   rax           |     eax       |     ax        |     al     |
                                |   rbx           |     ebx       |     bx        |     bl     |
                                |   rcx           |     ecx       |     cx        |     cl     |
                                |   rdx           |     edx       |     dx        |     dl     |
                                |   rsi           |     esi       |     si        |     sil    |
                                |   rdi           |     edi       |     di        |     dil    |
                                |   r8            |     r8d       |     r8w       |     r8b    |
                                |   r9            |     r9d       |     r9w       |     r9b    |
                                |   r10           |     r10d      |     r10w      |     r10b   |
                                |   r11           |     r11d      |     r11w      |     r11b   |
                                |   r12           |     r12d      |     r12w      |     r12b   |
                                |   r13           |     r13d      |     r13w      |     r13b   |
                                |   r14           |     r14d      |     r14w      |     r14b   |
                                |   r15           |     r15d      |     r15w      |     r15b   |
                                +-----------------+---------------+---------------+------------+

In x64 we will see the `8` byte registers. However, in x86 the largest registers we can use are the `4` byte registers like `ebp`, `esp`, `eip` etc. We can also use smaller registers than then maximum sized registers.

