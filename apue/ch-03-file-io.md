# 3. File I/O

- file descriptor: when we open an existing file or create a new file, the kernel returns a file descriptor to the process.
- `int open(const char *path, int oflag, mode_t mode)`: 
- `ssize_t read(int fd, void *buf, size_t nbytes)`: read at most `nbytes`. return the size of bytes read.
- `ssize_t write(int fd, const void *buf, size_t nbytes)`: 
- `off_t lseek(int fd, off_t offset, int whence)`: move the offset of fd. can be related to either start, current or end.
- `int close(int fd)`: 
- `dup`, `dup2`:
- `sync`: queue all modified block buffers for writing and returns.
- `fsync`, `fdatasync`: waits for write to disk finish and return.
- `int fcntl(int fd, int cmd, ... /* int arg */)`: modifies flag for files that are already opened
    - duplicate fd
    - get/set fd flags
    - get/set file status flags
    - get/set async. i/o ownership
    - get/set record locks
- `int ioctl(int fd, int request, ...)`: 

### data structures for open files in kernel

- process table entry: (per process)
    - fd
    - fd flags: close on exec
    - file pointer
- file table entry: 
    - file status flags: read, write, append, sync, nonblocking
    - current file offset
    - v-node pointer
- v-node table entry: 
    - v-node information
    - i-node pointer
- i-node: (file system data structure, not specific to open files) 
    - i_node information: owner
    - file size
    - v-node pointer
    

