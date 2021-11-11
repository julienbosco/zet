# Passing parameter in a C program

Here's an example:

```c
int
main (int argc, char *argv[])
{
  int counter;

    for (counter = 0; counter < argc; counter++)
        printf ("%s\n", argv[counter]);
          
            return 0;
            }
```

Related:

(https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html#The-main-Function)

