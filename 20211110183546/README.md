# Steps of compilation

main.c:

```c
int main() {
  return 0;
}
```

Using GCC, program's binary can be obtained with

    gcc main.c -o main

Code main.c is converted to x64 binary:

```
file main
main: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=48e5fcdda989f1843c7dd97f69c5b22a2a517c8e, not stripped
```

Return value can be obtain in Bash with `$?`:

    ./main; echo $?

To build a binary, the compiler breaks down the process in four primary steps:

* Pre-processor
* Compilation
* Assembly
* Linking

## Pre-processor

The first step prepare the source code to be compiled. This step resolve all line starting with an hashtag (#) like `#include` and `#define`.

Modify main.c:

```c
#define RETURNVALUE 0
int main() {
  return RETURNVALUE;
}
```

To see the result of the pre-processor step:

    gcc -E main.c -o main.i

Which get something like:

```

# 1 "main.c"
# 1 "<built-in>"
# 1 "<command-line>"
# 31 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 32 "<command-line>" 2
# 1 "main.c"

int main(void) {

  return 0;
}
```

To see how #include works, create `main.h`:
```c
int zero() { return 0; }
```
Adding `main.h` and call `zero()`:

```c
#include "main.h"
int main() { return zero(); }
```

The output of `main.i` is:

```
# 1 "main.c"
# 1 "<built-in>"
# 1 "<command-line>"
# 31 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 32 "<command-line>" 2
# 1 "main.c"
# 1 "main.h" 1
int zero() {
  return 0;
}
# 2 "main.c" 2
int main(void) {

  return zero();
}
```

The pre-processing step replace everything needed to get everything needed in one file in this case.

## Compilation

The compilation step takes output from pre-processing step and convert c language in assembly. Output is still a text file, nothing has been converted in binary format.

Compilation step in gcc is called with `-S` option:

    gcc -S main.i -o main.s

main.c can be used. Pre-processor step will be called before compilation step.

## Assembly

This step takes assembly code and then convert it to binary format. `-c` parameter assembles the program:

    gcc -c main.s -o main.o

Binary code can be viewed in hex format with `hexdump`:

    hexdump -C main.o

We can find some string present in `main.s`.
Also we can compare file type with a assembled and linked from the beginning:

```
file main.o
main.o: ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), not stripped
```

Here, `main.o` isn't linked like `main` from the beginning. This is the last step.

## Linking

Linking include or tell where to find functions called in executable but not available in produced code. This step is called in `GCC` when there's not option (but -o for output):

    gcc main.o -o main

Let's see what happen. First the size:

    ls -l main main.o
    -rwxr-xr-x 1 runner runner 8192 Nov 10 20:09 main
    -rwxr-xr-x 1 runner runner 1424 Nov 10 19:56 main.o
    
Linked file is way bigger. Dumping file give more information:

    objdump -d ./main

Stuff added is needed to interface OS. We can see library added with `ldd`:

    ldd ./main
    linux-vdso.so.1 (0x00007ffc7b2d1000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fcfceaea000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fcfcf0dd000)

Which are necessary for C code to run on Linux in this case.

Now, there's two way to link and add necessary code to executable. First is dynamically and second is statically.

### Dynamic

By default, `gcc` will compile with dynamic libraries. `ldd` shows used libraries.

### Static

GCC can compile statically with flag `--static`.
TODO: Check static compilation with `musl`. 


