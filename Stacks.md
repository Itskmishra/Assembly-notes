Stack is where local function variables in the code are stored. For instance, in this code, the variable `x` is stored in the stack:

```text-plain
#include <stdio.h>

void main(void)
{
    int x = 5;
    puts("hi");
}
```

Now we can see it is stored on the stack at `rbp-0x4`.

```text-plain
0000000000001135 <main>:
    1135:       55                      push   rbp
    1136:       48 89 e5                mov    rbp,rsp
    1139:       48 83 ec 10             sub    rsp,0x10
    113d:       c7 45 fc 05 00 00 00    mov    DWORD PTR [rbp-0x4],0x5
    1144:       48 8d 3d b9 0e 00 00    lea    rdi,[rip+0xeb9]        # 2004 <_IO_stdin_used+0x4>
    114b:       e8 e0 fe ff ff          call   1030 <puts@plt>
    1150:       90                      nop
    1151:       c9                      leave
    1152:       c3                      ret
    1153:       66 2e 0f 1f 84 00 00    nop    WORD PTR cs:[rax+rax*1+0x0]
    115a:       00 00 00
    115d:       0f 1f 00                nop    DWORD PTR [rax]
```

Values can be moved by either pushing the value onto the stack or poping the value onto the stack. That is the only way to add or remove values from the stack, as it is a FILO(First In, Last Out) data structure.

The exact bounds of the stack frame are recorded by two registers, `rbp` and `rsp`. The base pointer `rbp` points to the bottom of the stack. The stack pointer `rsp` points to the top of the stack.
