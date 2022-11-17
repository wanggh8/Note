# C 内存管理

C 语言的标准内存分配函数：`malloc`、`calloc`、`realloc`、`free` 等。

- malloc调用形式为 `(类型*)malloc(size)`：在内存的动态存储区中分配一块长度为 `size` 字节的连续区域，返回该区域的首地址。

- calloc调用形式为 `(类型*)calloc(n，size)`：在内存的动态存储区中分配n块长度为 `size` 字节的连续区域，返回首地址。

- realloc调用形式为 `(类型*)realloc(ptr，size)`：将 `ptr` 内存大小增大到 `size`。

- free的调用形式为 `free(voidptr)`：释放 `ptr` 所指向的一块内存空间。

C++ 对应为 `new`/ `delete` 函数。

## malloc 与 calloc 区别

### 相同点

都为了分配存储空间，它们返回的是 void * 类型，如果我们具体类型的数据分配空间必须显式强制转换

### 不同点

- malloc：一个形参，因此如果是数组，必须由我们计算需要的字节总数作为形参传递。
- calloc：2 个形参，因此如果是数组，需要传递个数和数据类型。

- 用 `malloc` 只分配空间不初始化，也就是依然保留着这段内存里的数据，
- 而 `calloc` 则进行了初始化，`calloc` 分配的空间全部初始化为 0，避免了可能的一些数据错误。

例如：分配 5 个 int 型的空间

```c
int *ptr;
// 未初始化，需手动初始化
ptr = (int *)malloc(sizeof(int) * 5);
// 已初始为 0
ptr = (int *)calloc(5, sizeof(int));
```
