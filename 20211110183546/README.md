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
## Compilation

## Assembly

## Linking

### Static

### Dynamic


