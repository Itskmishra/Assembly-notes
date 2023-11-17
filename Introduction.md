## So first off, what is assembly code? 

Assembly code is the code that is actually run on your computer by the processor. For instance, take some C code


        #include <stdio.h>
        
        void main(void)
        {
            puts("Hello World!");
        }


This code is not what runs. This code is compiled into assembly code, which looks like this:


      0000000000001135 <main>:
          1135:       55                      push   rbp
          1136:       48 89 e5                mov    rbp,rsp
          1139:       48 8d 3d c4 0e 00 00    lea    rdi,[rip+0xec4]        # 2004 <_IO_stdin_used+0x4>
          1140:       e8 eb fe ff ff          call   1030 <puts@plt>
          1145:       90                      nop
          1146:       5d                      pop    rbp
          1147:       c3                      ret
          1148:       0f 1f 84 00 00 00 00    nop    DWORD PTR [rax+rax*1+0x0]
          114f:       00


The purpose of languages like C is that we can program without having to really deal with assembly code. We write code that is handed to a compiler, and the compiler takes that code and generates assembly code that will accomplish whatever the C code tells it to.

