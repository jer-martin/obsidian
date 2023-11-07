### motd
last test case run:
```
Test Case: First Fit 1
memoryLimit: 26
bitmap: 00000000000000000000000000
allocating and freeing memory...
list: 1 0 208
size in words: 10
0
bitmap: 00000000000000001111111111
list: 11 0 7 8 7 16 7 24 7 32 7 40 7 48 7 56 7 64 7 72 7 80 128
size in words: 2
0
bitmap: 00000000000000001111111111
list: 11 0 7 8 7 16 7 24 7 32 7 40 7 48 7 56 7 64 7 72 7 80 128
size in words: 2
0
bitmap: 00000000000000001111111111
list: 11 0 7 8 7 16 7 24 7 32 7 40 7 48 7 56 7 64 7 72 7 80 128
size in words: 6
0
bitmap: 00000000000000001111111111
expected correctBitmap.size(): 4
Testing Memory Manager state after allocations and frees

list: 11 0 7 8 7 16 7 24 7 32 7 40 7 48 7 56 7 64 7 72 7 80 128
Testing getList
Expected:
[0] - [10] - [12] - [2] - [20] - [6]

Got:
[0] - [7] - [8] - [7] - [16] - [7] - [24] - [7] - [32] - [7] - [40] - [7] - [48] - [7] - [56] - [7] - [64] - [7] - [72] - [7] - [80] - [128]
[INCORRECT]

testBitmap:
00000000 11001100 00001111 00000000
Score: 0 / 38
```

currently the offset is hardcoded to 0 (this needs to be fixed). but before I can fix that, I need to fix the getList (this may actually require fixing getHoles), as it should not be returning 11 holes on the second bitmap. it seems to work when its empty, but once it hits a 1 it wants to split everything into lengths of 7? this may have something to do with the bitwise stepping thru the bitmap
i think i need the night to think about it

1. **Basic Setup**:
    - [x]  Implement verbose constructor `MemoryManager(unsigned wordSize, std::function allocator)`
    - [x]  Implement destructor `~MemoryManager()`
    - [x]  Implement initialization `initialize(size_t sizeInWords)`
    - [x]  Implement shutdown `shutdown()`
    - [x]  Implement getWordSize `unsigned getWordSize()`
    - [x]  Implement getMemoryStart `void getMemoryStart()`
  
2. **Memory Allocation Algorithms**:
    - [x]  Implement best fit `int bestFit(int sizeInWords, void *list)`
    - [x]  Implement worst fit `int worstFit(int sizeInWords, void *list)`

3. **Core Memory Operations**:
    - [x]  Implement allocation `void *allocate(size_t sizeInBytes)`
    - [x]  Implement freeing `void free(void *address)`

4. **Setting Allocation Strategy**:
    - [x]  Implement setAllocator `void setAllocator(std::function<int(int, void *)> allocator`

5. **Memory Reporting and Diagnostics**:
    - [ ]  Implement getList (ensure to return in decimal) `void *getList()`
    - [ ]  Implement getBitmap `void *getBitmap()`
    - [x]  Implement dumpMemoryMap `int dumpMemoryMap(char * filename)`

6. **Memory Information Retrieval**:
    - [x]  Implement getMemoryLimit `unsigned getMemoryLimit()`