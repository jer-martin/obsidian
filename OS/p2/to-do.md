- [x] implement verbose constructor
``` public MemoryManager(unsigned wordSize, std::function allocator)```

- [x] implement destructor 
```public ~MemoryManager();```

- [x] implement initialization
```public void initialize(size_t sizeInWords)```

- [x] implement shutdown
```public void shutdown()```

- [ ] implement mem allocation algorithms
	- [ ] best fit
		``` int bestFit(int sizeInWords, void *list)```
	- [ ] worst fit
		```int worstFit(int sizeInWords, void *list)```


- [ ] implement allocation
```public void *allocate(size_t sizeInBytes)```

- [ ] implement freeing
```public void free(void *address)```

- [ ] implement setAllocator
```public void setAllocator(std::function<int(int, void *)> allocator*```

- [ ] implement dumpMemoryMap
```public int dumpMemoryMap(char * filename)```

- [ ] implement getList
```public void *getList()```
*note: this should return in decimal*

- [ ] implement getBitmap
```public void *getBitmap()```

- [x] implement getWordSize
```public unsigned getWordSize()```

- [x] implement getMemoryStart
```public void getMemoryStart()```

- [ ] implement getMemoryLimit 
```public unsigned getMemoryLimit()```