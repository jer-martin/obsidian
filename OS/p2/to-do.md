### motd
nothing as of yet

1. **Basic Setup**:
    - [x]  Implement verbose constructor `MemoryManager(unsigned wordSize, std::function allocator)`
    - [x]  Implement destructor `~MemoryManager()`
    - [x]  Implement initialization `initialize(size_t sizeInWords)`
    - [x]  Implement shutdown `shutdown()`
    - [x]  Implement getWordSize `unsigned getWordSize()`
    - [x]  Implement getMemoryStart `void getMemoryStart()`
  
2. **Memory Allocation Algorithms**:
    - [x]  Implement best fit `int bestFit(int sizeInWords, void *list)`
    - [ ]  Implement worst fit `int worstFit(int sizeInWords, void *list)`

3. **Core Memory Operations**:
    - [ ]  Implement allocation `void *allocate(size_t sizeInBytes)`
    - [ ]  Implement freeing `void free(void *address)`

4. **Setting Allocation Strategy**:
    - [x]  Implement setAllocator `void setAllocator(std::function<int(int, void *)> allocator`

5. **Memory Reporting and Diagnostics**:
    - [ ]  Implement getList (ensure to return in decimal) `void *getList()`
    - [ ]  Implement getBitmap `void *getBitmap()`
    - [ ]  Implement dumpMemoryMap `int dumpMemoryMap(char * filename)`

6. **Memory Information Retrieval**:
    - [x]  Implement getMemoryLimit `unsigned getMemoryLimit()`