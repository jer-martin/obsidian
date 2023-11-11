### Test Results Summary

#### Passed Tests
- [x] Test Case: First Fit 1
- [x] Test Case: Best Fit 1
- [x] Test Case: Best Fit 2
- [x] Test Case: New allocator
- [x] Test Case: invalid allocation, over the allowed amount
- [x] Test Case: testGetters, wordSize = 8, numberOfWords = 26

#### Failed Tests
- [ ] Test Case: repeated shutdown
  - Testing getBitmap
    - Expected: `[0x71, 0x0, 0x0]`
    - Got: `[0x3, 0x3f, 0x0]`
  - Testing getList
    - Expected: `[1] - [3] - [7] - [13]`
    - Got: `[2] - [6] - [14] - [6]`
  - Testing dumpMemoryMap
    - Expected: `[1, 3] - [7, 13]`
    - Got: `[2, 6] - [14, 6]`
- [ ] Test Case: max initialization
  - No specific expected and received values provided
- [ ] Test Case: Reading memory using GetMemoryStart
  - Testing Memory Value
    - Expected: `1`
    - Got: `2199023255553`

#### Overall Score
28 / 38
