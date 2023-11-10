### Failed Test Results

#### Test Case: First Fit 1
- [ ] Testing getList
  - Expected: [0] - [10] - [12] - [2] - [20] - [6]
  - Got: [0] - [10] - [12] - [2] - [20] - [12]
- [ ] Testing dumpMemoryMap
  - Expected: [0, 10] - [12, 2] - [20, 6]
  - Got: [0, 10] - [12, 2] - [20, 12]

#### Test Case: repeated shutdown
- [ ] Testing getBitmap
  - Expected: [0x71, 0x0, 0x0]
  - Got: [0x3, 0x3f, 0x0]
- [ ] Testing getList
  - Expected: [1] - [3] - [7] - [13]
  - Got: [2] - [6] - [14] - [10]
- [ ] Testing dumpMemoryMap
  - Expected: [1, 3] - [7, 13]
  - Got: [2, 6] - [14, 10]

#### Test Case: max initialization
- [ ] Testing getMemoryLimit
  - Expected: 208
  - Got: 32

#### Test Case: Reading memory using GetMemoryStart
- [ ] Testing Memory Value
  - Expected: 1
  - Got: 2199023255553
