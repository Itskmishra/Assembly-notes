We will be covering some of the more common instructions in x86 Intel syntax. This isn't even close to every instruction , just the often used ones. There's an incredible number of instructions but there's only a few that are worth memorizing, the rest can go on cheat sheets or you can look them up as you go.

Here's a list of instructions we will be covering:

```text-plain
mov
lea
add
sub
xor
push
pop
jmp
call
ret
cmp
jnx/jz
```

mov
---

The move instruction just moves data from one register to another.

```text-plain
mov rax, rdx
```

This will just move data from second register into first argument.

lea
---

The lea instruction calculates the address of the second operand, and moves that address in the first.

```text-plain
lea rdi, [rbx+0x10]
```

This will move the address `[rbx+0x10]` into `rdi` register.

add
---

This just adds the two values and stores the sum in the first agrugment.

```text-plain
add rax, rdx
```

this will set the value `rax` to `rax + rdx`.

sub
---

This will subtract the second operand from the first one and store it in the first argument.

```text-plain
sub rsp, 0x10
```

this will set the value of `rsp` to `rsp - 0x10` .

xor
---

This will perform binary operation on the arguments  and store the result in the first argument.

```text-plain
xor rdx, rax
```

This will set the `rdx` register equal to `rdx ^ rax`. If the `xor` instruction is used with the same register for both argument, for example `xor rax, rax`, it will set all bits to zero, clearing the register. This is the most used case for `xor`.

push
----

The push instruction will grow the stack by either `8` bytes (for `x64,` `4` for `x86`), then push the contents of a register onto the new stack space.

```text-plain
push rax
```

this will grow the stack by `8` bytes, and the content of the `rax` register will be on top of the stack.

pop
---

The `pop` instruction will pop the top `8` bytes (for `x64`, `4` for `x86`) off of the stack and into the argument. Then it will shrink the stack. 

```text-plain
pop rax
```

the top `8` bytes of the stack will end up in the `rax` register.

jmp
---

The `jmp` instruction will jump to an instruction address. It is used to redirect code execution. 

```text-plain
jmp 0x602010
```

that instruction will cause the code execution to jump to `0x602010`, and execute whatever instruction is there.

call & ret
----------

This is similar to the `jmp` instruction. The difference is it will push the values of `rbp` and `rip` onto the stack, then jump to whatever address it is given. This is used for calling functions. After the function is finished, a `ret` instruction is called which uses the pushed values of `rbp` and `rip` (saved base and instruction pointers) to return, it can continue execution right where it left off.

cmp
---

The cmp instruction is similar to that of the sub instruction. Except it doesn't store the result in the first argument. It checks if the result is less than zero, greater than zero, or equal to zero. Depending on the value it will set the flags accordingly.

jnz / jz
--------

The `jump if not zero` and `jump if zero` (`jnz/jz`) instructions are pretty similar to the jump instruction. The difference is they will only execute the jump depending on the status of the `zero` flag. For `jz` it will only jump if the `zero` flag is set. The opposite is true for `jnz`. These instructions are how control flow is implemented in assembly.
