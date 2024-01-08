makefile steps:

```
g++ -std=c++17 -c MemoryManager/MemoryManager.cpp -o MemoryManager/MemoryManager.o
```

```
g++ -std=c++17 -c MemoryManager/MemoryAlgorithms.cpp -o MemoryManager/MemoryAlgorithms.o
```

```
ar rcs MemoryManager/libMemoryManager.a MemoryManager/MemoryManager.o MemoryManager/MemoryAlgorithms.o
```

```
g++ -g -std=c++17 -o cmdline CommandLineTest.cpp -LMemoryManager -lMemoryManager
```