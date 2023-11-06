Part 1: 
```
  @Test 
	public void testReverseInPlace2() {
    int[] input1 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2, 1}, input1);
	}
```
This is a test I wrote for the reverseInPlace method, where the expected output is the array {3, 2, 1}, but the actual output is {3, 2, 2}.
