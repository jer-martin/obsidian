memoryLimit: 100





memory was allocated. shutting down...
Test Case: First Fit 1
memoryLimit: 26
allocating and freeing memory...


Testing Memory Manager state after allocations and frees
bitmapSize: 4
00000100 00000000 00000000 11001100 00001111 00000000
Testing getBitmap
Expected:
[0x0, 0xcc, 0xf, 0x0]

Got:
[0x0, 0xcc, 0xf, 0x0]
[CORRECT]


Testing getList
Expected:
[0] - [10] - [12] - [2] - [20] - [6]

Got:
[0] - [10] - [12] - [2] - [20] - [6]
[CORRECT]

Testing dumpMemoryMap
Expected: [0, 10] - [12, 2] - [20, 6]
Got:[0, 10] - [12, 2] - [20, 6]
[CORRECT]

Score: 3 / 38
Test Case: Best Fit 1
memoryLimit: 96


allocating 4 words
Testing Memory Manager state after allocation
bitmapSize: 12
00001100 00000000 00001111 11111110 00000011 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
Testing getBitmap
Expected:
[0xf, 0xfe, 0x3, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0]

Got:
[0xf, 0xfe, 0x3, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0]
[CORRECT]


Testing getList
Expected:
[4] - [5] - [18] - [78]

Got:
[4] - [5] - [18] - [78]
[CORRECT]

Testing dumpMemoryMap
Expected: [4, 5] - [18, 78]
Got:[4, 5] - [18, 78]
[CORRECT]

Score: 6 / 38
Test Case: Best Fit 2
memoryLimit: 48
no hole found. cannot allocate
no hole found. cannot allocate
Testing Memory Manager state after initial allocations
bitmapSize: 6
00000110 00000000 11111111 11111111 11111111 11111111 11111111 00000000
Testing getBitmap
Expected:
[0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xf, 0x0, 0x0, 0x0, 0x0]

Got:
[0xff, 0xff, 0xff, 0xff, 0xff, 0x0]
[INCORRECT]


Testing getList
Expected:
[60] - [36]

Got:
[40] - [8]
[INCORRECT]





Testing Memory Manager state after freeing specific areas
bitmapSize: 6
00000110 00000000 11111111 11000011 11111111 11111000 00011111 00000000
Testing getBitmap
Expected:
[0xff, 0xc3, 0xff, 0xf8, 0x9f, 0xff, 0xfd, 0xf, 0x0, 0x0, 0x0, 0x0]

Got:
[0xff, 0xc3, 0xff, 0xf8, 0x1f, 0x0]
[INCORRECT]


Testing getList
Expected:
[10] - [4] - [24] - [3] - [37] - [2] - [49] - [1] - [60] - [36]

Got:
[10] - [4] - [24] - [3] - [37] - [11]
[INCORRECT]

Allocating 1 words
Testing Memory Manager state

bitmapSize: 6
00000110 00000000 11111111 11000011 11111111 11111001 00011111 00000000
Testing getBitmap
Expected:
[0xff, 0xc3, 0xff, 0xf8, 0x9f, 0xff, 0xff, 0xf, 0x0, 0x0, 0x0, 0x0]

Got:
[0xff, 0xc3, 0xff, 0xf9, 0x1f, 0x0]
[INCORRECT]


Testing getList
Expected:
[10] - [4] - [24] - [3] - [37] - [2] - [60] - [36]

Got:
[10] - [4] - [25] - [2] - [37] - [11]
[INCORRECT]

Allocating 2 words
Testing Memory Manager state

bitmapSize: 6
00000110 00000000 11111111 11000011 11111111 11111111 00011111 00000000
Testing getBitmap
Expected:
[0xff, 0xc3, 0xff, 0xf8, 0xff, 0xff, 0xff, 0xf, 0x0, 0x0, 0x0, 0x0]

Got:
[0xff, 0xc3, 0xff, 0xff, 0x1f, 0x0]
[INCORRECT]


Testing getList
Expected:
[10] - [4] - [24] - [3] - [60] - [36]

Got:
[10] - [4] - [37] - [11]
[INCORRECT]

Allocating 3 words
Testing Memory Manager state

bitmapSize: 6
00000110 00000000 11111111 11011111 11111111 11111111 00011111 00000000
Testing getBitmap
Expected:
[0xff, 0xc3, 0xff, 0xff, 0xff, 0xff, 0xff, 0xf, 0x0, 0x0, 0x0, 0x0]

Got:
[0xff, 0xdf, 0xff, 0xff, 0x1f, 0x0]
[INCORRECT]


Testing getList
Expected:
[10] - [4] - [60] - [36]

Got:
[13] - [1] - [37] - [11]
[INCORRECT]

Allocating 4 words
Testing Memory Manager state

bitmapSize: 6
00000110 00000000 11111111 11011111 11111111 11111111 11111111 00000001
Testing getBitmap
Expected:
[0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xff, 0xf, 0x0, 0x0, 0x0, 0x0]

Got:
[0xff, 0xdf, 0xff, 0xff, 0xff, 0x1]
[INCORRECT]


Testing getList
Expected:
[60] - [36]

Got:
[13] - [1] - [41] - [7]
[INCORRECT]

Testing dumpMemoryMap
Expected: [60, 36]
Got:[13, 1] - [41, 7]
[INCORRECT]

Score: 6 / 38
Test Case: New allocatormemoryLimit: 88



Allocating 4 words
Testing Memory Manager state

bitmapSize: 11
00001011 00000000 11111111 00000011 10000000 11111111 00000001 11111110 10000111 11111111 00011111 00000000 00000000
Testing getBitmap
Expected:
[0xff, 0x3, 0x80, 0xff, 0x1, 0xfe, 0x87, 0xff, 0x1f, 0x0, 0x0]

Got:
[0xff, 0x3, 0x80, 0xff, 0x1, 0xfe, 0x87, 0xff, 0x1f, 0x0, 0x0]
[CORRECT]


Testing getList
Expected:
[10] - [13] - [33] - [8] - [51] - [4] - [69] - [19]

Got:
[10] - [13] - [33] - [8] - [51] - [4] - [69] - [19]
[CORRECT]

Allocating 4 words
Testing Memory Manager state

bitmapSize: 11
00001011 00000000 11111111 00111111 10000000 11111111 00000001 11111110 10000111 11111111 00011111 00000000 00000000
Testing getBitmap
Expected:
[0xff, 0x3f, 0x80, 0xff, 0x1, 0xfe, 0x87, 0xff, 0x1f, 0x0, 0x0]

Got:
[0xff, 0x3f, 0x80, 0xff, 0x1, 0xfe, 0x87, 0xff, 0x1f, 0x0, 0x0]
[CORRECT]


Testing getList
Expected:
[14] - [9] - [33] - [8] - [51] - [4] - [69] - [19]

Got:
[14] - [9] - [33] - [8] - [51] - [4] - [69] - [19]
[CORRECT]

Allocating 4 words
Testing Memory Manager state

bitmapSize: 11
00001011 00000000 11111111 00111111 10000000 11111111 00011111 11111110 10000111 11111111 00011111 00000000 00000000
Testing getBitmap
Expected:
[0xff, 0x3f, 0x80, 0xff, 0x1f, 0xfe, 0x87, 0xff, 0x1f, 0x0, 0x0]

Got:
[0xff, 0x3f, 0x80, 0xff, 0x1f, 0xfe, 0x87, 0xff, 0x1f, 0x0, 0x0]
[CORRECT]


Testing getList
Expected:
[14] - [9] - [37] - [4] - [51] - [4] - [69] - [19]

Got:
[14] - [9] - [37] - [4] - [51] - [4] - [69] - [19]
[CORRECT]

Testing dumpMemoryMap
Expected: [14, 9] - [37, 4] - [51, 4] - [69, 19]
Got:[14, 9] - [37, 4] - [51, 4] - [69, 19]
[CORRECT]

Score: 13 / 38
Test Case: invalid allocation, over the allowed amount
memoryLimit: 5
no hole found. cannot allocate
[INCORRECT]

memory was allocated. shutting down...
Score: 13 / 38
Test Case: repeated shutdown
Generating Memory Manager...
memoryLimit: 2
no hole found. cannot allocate

(infinitely hung here)