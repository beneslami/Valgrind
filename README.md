### Common Memory Issues in C Programming

* Incorrect Memory accesses
1. Using un-initialized variables
2. Out-of-bounds memory accesses (read/write underflow/overflow bugs)
3. Use-after-free/use-after-return (out-of-scope) bugs
4. Double free

* Leakage

* Undefined Behavior

* Data races

Operating upon a memory pointer after it has been freed up is obviously a bug. The pointer is sometimes called a **dangling Pointer**.

Valgrind is a debugging tool. It is a wrapper around various tools for debugging and profiling. It is without a doubt the best tool out of these is MmeCheck that is used to find out memory leaks, etc. In order to use Valgrind, we have to include debugging information that is we should compile the application with -g option if we are using gcc.

```
$ valgrind --tool=memcheck --leak-check=yes <binary file>
```
Pros:
It catches common memory bugs on dynamically allocated memory regions
* using uninitialized variables
* out-of-bounds memory access(read/write underflow/overflow bugs)
* Use-after-free/use-after-return (out of scope) bugs
* Double free
* Leakage

Cons:
Performance: target software may run up to 10 to 30 times slower when run under valgrind

Memory footprint: each allocation within the target program requires valgrind to make a memory allocation as well (making running valgrind on highly-resource-constrained embedded linux systems difficult).

In order to see the call stack with line-numebr information, a recompile/build with the -g flag is required.
