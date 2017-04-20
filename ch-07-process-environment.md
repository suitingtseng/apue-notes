# 7. Process Environment

- `exit(int status)`: exit handlers then `fclose` on all open stream.
- `_exit(int status)`, `_Exit(int status)`: return to kernel directly
- `atexit`: put a function(exit handler) on stack(LIFO). executed when exit.
- Exit handlers are cleaned when `exec` is called.
- Environment list: list of strings. Interpretation is application-dependent.


### Memory Layout (from low address to high address)

- text segment: instructions. read from program file.
- initialized data segment: global variable like `int`. read from program file.
- uninitialized data segment (bss): global variable like `array of ing`. initialized to zero by exec.
- heap: from `new`, `malloc`.
- stack: auto variable in function.
- command-line arguments and environment variables: 

- `size(1)` reports the sizes of the text, data and bss segments.

### Memory Allocation

- `malloc(size_t size)`: get a memory of size. may be from `sbrk` or the memory pool.
- `free`, `realloc(void *ptr, size_t newsize)`: usually doesn't return memory to kernel. maintain a pool for itself for later use.
- `sbrk`: system call to expand or contract heap size for process.

### rlimit

- `getrlimit`
- `setrlimit`
- soft limit and hard limit
