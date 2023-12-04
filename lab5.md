Lab Report 5

Part 1: Debugging Scenario

1. Student Post:
Hi, I am currently attempting working on implementing a merge method for mergeSort, but the method keeps failing the test I wrote. I'm not sure what I did wrong, so I would love some help on fixing this bug. Here is what I've written so far:
My code:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/00eebad1-d604-4056-b96d-6678dc6a4225)
The code I wrote to test the command:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/63970bc6-f369-41ce-85f2-8ad89c32d5d1)
The commands I ran and the output:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/3421b65a-3b01-4e8c-9159-af97c60512c0)

If I had to guess what the bug was for the code, I would assume there was something off about how I'm iterating through the arrays, as the code runs for a long time before finally producing the error and the symptom itself says that the heap ran out of memory. However, I'm really struggling to identify the issue.
Thanks,
Confused Student
2. TA response:
Hi Confused, your guess at what might be the issue is mostly correct. To start, consider going back and reviewing how the merge part of mergeSort works. In your implementation, you're comparing elements in one list to another with pointers going through each list until one pointer has traversed through the whole array. Then, you add in all the remaining elements of the not fully traversed array. To fix your code, I'd recommend double checking that all of your index variables are being incremented at the right positions, since if one is not being incremented when it should be, it could form arrayLists way larger or smaller than intended. Consider tracing your code carefully, and seeing if you end up stuck. Good luck on writing your code!
Thanks,
Tea Ay
3. Student Attempt:
After reviewing what the TA had said and tracing their code, the student realized that they had used the wrong index in the final part of his method, having used index1 instead of index2. After trying out their new code, they discovered that they had another bug, this time due to his test; the test was outputting the memory address of the array instead of its contents, and student added in a call to Arrays.toString() to fix this as well. Here was their final result:
Code:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/21eca28b-7dbf-4930-91a6-a12ef8593407)
Test:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/dd0b3f0e-44cb-48c5-8439-47f60ced820f)
Output:
![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/0e1b1d4a-26dc-4603-a73a-5a1666dfa7f0)
4. Final setup:
Directory:
```
Lab Report 5/
|-- MergeSort.java
|-- MergeTest.java
```
MergeSort:
```
import java.util.ArrayList;
import java.util.List;

class MergeSort {

  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));

      index1 += 1;
    }
    return result;
  }

}
```
MergeTest:
```
import java.util.*;
import java.util.ArrayList;


public class MergeTest {

    public static void main(String [] args) {
		List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
		List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
		System.out.println(MergeSort.merge(l1,l2).toArray());
	}

}
```
Terminal Commands:
```
javac *.java
java MergeTest.java
```
To fix the bug, change index1 in line 26 of MergeSort.java to index2.

Part 2: Reflection
I think the coolest thing I learned in the second half of the quarter was how to use Vim and edit code directly from the command line. While I can appreciate all the shortcuts/hotkeys Vim has to speed up programming, I think what I liked best about it was how one can make quick edits on the fly without having to open the IDE and go through the whole process of editing code that way.
