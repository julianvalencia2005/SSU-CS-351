## Which program is fastest? Is it always the fastest?

In my tests, `alloca.out` was usually one of the fastest programs. This makes sense because it allocates memory on the stack instead of using heap allocation, which can reduce allocation overhead. However, it may not always be the fastest for every configuration because performance can change depending on optimization level, node size, and number of blocks.

## Which program is slowest? Is it always the slowest?

In my tests, `new.out` was usually slower, especially with larger block counts. This is likely because it manually creates many heap-allocated nodes using `new`, which adds overhead for every node. It is not guaranteed to always be the slowest, but it tended to perform worse as the linked list grew.

## Was there a trend in program execution time based on the size of data in each Node? If so, what, and why?

Yes. As the amount of data in each node increased, the execution time also increased. This happens because each node has more bytes to allocate, initialize, store, and hash. Larger nodes also use more memory, which can reduce cache efficiency and make memory access slower.

## Was there a trend in program execution time based on the length of the block chain?

Yes. As the number of blocks increased, the execution time increased. This is expected because the programs must create more nodes and process more data. A longer linked list means more allocations, more pointer traversal, and more hashing work.

## Consider heap breaks, what's noticeable? Does increasing the stack size affect the heap? Speculate on any similarities and differences in programs?

The heap break results show how often the program needed to request more heap memory from the operating system. Programs using heap allocation, like `malloc.out`, `new.out`, and `list.out`, are more connected to heap growth. `alloca.out` uses stack memory instead, so increasing the stack size helps `alloca.out` handle larger recursive stack allocations, but it does not directly increase or change the heap. The programs are similar because they all build a linked list and compute the same hash, but they differ in where and how memory is allocated.

## Diagram of two Nodes

Example using `malloc.cpp` with a Node that allocated 6 bytes of data:
head
|
v
+-------------------+ +-------------------+
| Node 1 | | Node 2 |
| next ------------ |------> | next ------------ |----> nullptr
| bytes pointer ----|--+ | bytes pointer ----|--+
+-------------------+ | +-------------------+ |
v v
allocated data allocated data
+---+---+---+---+---+---+ +---+---+---+---+---+---+
| 1 | 2 | 3 | 4 | 5 | 6 | | 1 | 2 | 3 | 4 | 5 | 6 |
+---+---+---+---+---+---+ +---+---+---+---+---+---+
^
|
bytes points here

tail -------------------------------> Node 2

The `head` pointer points to the first node. The first node’s `next` pointer points to the second node. The second node’s `next` pointer is `nullptr`. The `tail` pointer points to the last node.

## There's an overhead to allocating memory, initializing it, and eventually processing it. For each program, were any of these tasks the same? Which ones were different?

All four programs do the same general work: they create nodes, initialize byte data, and hash the data. The hashing work is mostly the same because each program processes the same generated data. The main difference is memory allocation. `list.cpp` uses `std::list` and `std::vector`, `new.cpp` uses `new`, `malloc.cpp` uses `malloc()` with placement `new`, and `alloca.cpp` uses stack allocation with `alloca()`. Because the allocation strategy is different, the overhead is different.

## As the size of data in a Node increases, does the significance of allocating the node increase or decrease?

As the size of data in each node increases, the relative significance of the node allocation usually decreases. For small nodes, allocation overhead is a major part of the total runtime. For larger nodes, more time is spent initializing and hashing the bytes, so the allocation cost becomes a smaller percentage of the total work.
