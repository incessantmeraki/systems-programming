## Data types

- Scalar: char, short, int, long, float, double
- Aggregate: struct
- Pointers

## Memory

- char: 1 byte (%c)
- short: 2 bytes 
- int: 4 bytes (%d, %x)
- long: 4/8 bytes (%ld, %lx)
- float: 4 bytes
- double: 8 bytes
- pointer: 4/8 bytes (%lx)

## Use of typedef

Use with structs
```c
typdef struct {
  int x;
  int y;
} Position;
```
Use with scalar type
```c
typedef unsigned long UL
```

## Buffer Overflow

Care must be taken while reading strings using scanf into chracter array. If the size of the input string exceed the expected size then the characters will use/overwrite the memory that is not intented for it.

```c
#include <stdio.h>
#include <stdlib.h>

main()
{
  char s1[10];
  char s2[10];
  int i;
  
  printf("s1: 0x%lx\n", (unsigned long) s1);
  printf("s2: 0x%lx\n", (unsigned long) s2);

  printf("\nEnter s1 and s2:\n\n");
  
  if (scanf("%s", s1) != 1) exit(0);
  if (scanf("%s", s2) != 1) exit(0);

  printf("\n");
  printf("s1: %s\n", s1);
  printf("s2: %s\n", s2);
}
```
## Segmentation and Bus Error

- Segmentation error occurs when accessing inaccessible part of memory. Usually the 0 to 0x1000 indices of memory are inaccessible and trying to access them results in segmentation voilation.
- Generally data are stored at position which is multiple of 4. Trying to access memory index which is not multiple of 4 results in bus error which happens in some system

## Type Casting/Coersion

- Compiler automatically casts from lower to higher. Example: int -> long
- To cast from higher data type to lower make use of explicit casting 
```c
double a = 13.444;
int b = (int) a // Here a is type casted from double to integer
```
