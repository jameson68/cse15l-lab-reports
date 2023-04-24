# Part 1

# Part 2
I am choosing the code of ReverseInPlace:

* A failure-inducing input for the buggy program, as a JUnit test and any associated code:
```
# code block
  @Test
  public void testReverseInPlaceLargeArray() {
    int[] input = {1, 2, 3, 4, 5, 6, 7};
    int[] output = {7, 6, 5, 4, 3, 2, 1};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(output, input);
 }
```
* An input that doesn’t induce a failure, as a JUnit test and any associated code:
```
# code block
  @Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```
* The symptom, as the output of running the tests:
1. The first test run into a failure as shown below
![Image](symptom.jpg)
2. The second test didn't run into a failure.
* The bug, as the before-and-after code change required to fix it:

1. The before code as shown below:
```
#code block
 static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
2. The after code as shown below:
```
#code block
 static void reverseInPlace(int[] arr) {
   for (int i = 0; i < arr.length / 2; i++) {
     int temp = arr[i];
     arr[i] = arr[arr.length - i - 1];
     arr[arr.length - i - 1] = temp;
   }
 }
```
# Part 3
