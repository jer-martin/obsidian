```
g++ -std=c++17 -c MemoryManager/MemoryManager.cpp -o MemoryManager/MemoryManager.o
```

```
g++ -std=c++17 -o cmdline CommandLineTest.cpp -L ./MemoryManager -lMemoryManager
```

```
ar rcs MemoryManager/libMemoryManager.a MemoryManager/MemoryManager.o
```

