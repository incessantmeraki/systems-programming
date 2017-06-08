## Data types

- Scalar: char, short, int, long, float, double
- Aggregate: struct
- Pointers

## Memory

- char: 1 byte (%c)
- short: 2 bytes 
- int: 4 bytes (%d, %x)
- long: 4/8 bytes (%ld, %lx)
- float: 4 bytes (%f)
- double: 8 bytes (%lf)
- pointer: 4/8 bytes (%lx)

Verify the size of data type using sizeof.
```c
printf("The size of long in my CPU is %ld.", sizeof(long));
```

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

Care must be taken while reading strings using scanf . If the size of the input string exceed the expected size then the characters will use/overwrite the memory that is not intented for it.

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
## Memory

Memory is an array of bytes that go from 0 to 0xffffffff on 32-bit architecture and from 0 to 0xffffffffffffffff on 64-bit architecture. However, all the indices of array are not valid.  

### Allocating memory

It is done using malloc and malloc assures returns a pointer which is a multiple of 8.

```c
int *a;
a = (int *) malloc(sizeof(int))
```

### Memory Layout

Memory is byte addressable.
```
|byte1|byte2|byte3|byte4|
|   a |   b |  c  |  d  | 

if bp, ip points to start of above memory(array)

char *bp;
int  *ip;

Deferencing:
bp => a
ip => dcba
```

In above ip returns dcba instead of abcd. This is called little-endian format followed by the memory. 

## Pointer Arithmetic 

When you add x to a pointer then you actually add ax where a = sizeof(pointer data_type)

```c
int *ip;
printf("%ld", ip); //ip = 4
ip++; // does pointer arithmetic
printf("%ld", ip); //now ip = 8 
```

For example:
```c
typedef struct {
  int x;
  int y;
}coordinate; //sizeof(cooridnate) = 4 + 4 = 8 bytes


int main()
{
  coordinate *p;
  printf("ld\n",p) //p  = 4
  p++; // p = p + (sizeof(coordinate)x 1)
  printf("ld\n",p); // p = 12
```
