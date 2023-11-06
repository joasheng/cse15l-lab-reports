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
```
@Test
public void testReverseInPlace2() {
  int[] input1 = {1};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{1}, input1);
}
```
This test would not fail despite the buggy implementation, as it is the case where there is only one value in the array list and there is nothing to be overwritten.

![image](https://github.com/joasheng/cse15l-lab-reports/assets/125727125/ad3824d5-b6f1-4539-981b-cdb12514ca12)
Here is the symptom, where the last element in the output array differs by being 3 instead of 1.

Before Implementation:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
After Implementation:
```
  static void reverseInPlace(int[] arr) {
    int[] temp = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      temp[i] = arr[i];
    }
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = temp[arr.length - i - 1];
    }
  }
```
This fixes the method as the original array is copied to a new, temporary array to prevent data from being overwritten. In the buggy implementation, some of the starting values in the array would get overwritten by the reversed values before they could be copied.

Part 2:
I am researching the find command
1. -exec grep -Hi content {} \;
This option searches the content of each file - replace content with the word you wish to search for
Example 1:
```
$ find ./technical/911report  -exec grep -Hi Usama {} \;
grep: ./technical/911report: Is a directory
./technical/911report/chapter-11.txt:                spark a full public discussion of who Usama Bin Ladin was, what kind of organization
./technical/911report/chapter-11.txt:                sentence:"Iran and its surrogates, as well as terrorist financier Usama Bin Ladin
./technical/911report/chapter-12.txt:            As we mentioned in chapter 2, Usama Bin Ladin and other Islamist terrorist leaders
./technical/911report/chapter-12.txt:                interests long after Usama Bin Ladin and his cohorts are killed or captured. Thus
./technical/911report/chapter-12.txt:                terrorists, many Taliban fighters, and-perhaps-Usama Bin Ladin. Pakistan possesses
./technical/911report/chapter-12.txt:            The small percentage of Muslims who are fully committed to Usama Bin Ladin's vers
```
As you can see, every file in this directory that contains the keyword "Usama" is returned, and the relevant lines are also shown. This is useful if you need to find a file containing specific information, without manually searching through each file in the directory.
Example 2:
```
$ find ./technical/911report  -exec grep -Hi "Usama Bin Laden" {} \;
grep: ./technical/911report: Is a directory
./technical/911report/chapter-13.3.txt:            30. Trial testimony of Jamal al Fadl, United States v. Usama bin Laden, No. S(7) 98
./technical/911report/chapter-13.3.txt:                FBI Special Agent Daniel Coleman, United States v. Usama Bin Laden, No. S(7) 98 Cr.
./technical/911report/chapter-13.3.txt:            109. Indictment, United States v. Usama Bin Laden, No. 98 Cr. (S.D. N.Y. unsealed
./technical/911report/chapter-13.4.txt:                memo,"U.S. Engagement with the Taliban on Usama Bin Laden," undated (attached to NSC
```
This time, quotes are added to search for an entire phrase instead of separate words (leaving out the quotes prints out each file that contains at least one of the words in the arguments). 
2. -type 
This option allows one to search by type
Example 1:
```
$ find ./technical -type d
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
```
By adding -type d, we managed to keep only the directories within the technical directory. 

Example 2: 
```
$ find ./technical/911report -type f
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
./technical/911report/preface.txt
```
Here, we've kept only files, leaving out the directories instead.

3. -mtime
This option allows one to filter files by time last edited/modified
Example 1:
```
$ find ./technical/911report -type f -mtime -1
./technical/911report/chapter-1.txt
```
This command only shows files that have been edited in the last day. Here, I edited the file so it would show up; all other files had not been modified in the past day.
Example 2:
```
$ find ./technical/911report -type f -mtime -7
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
./technical/911report/preface.txt
```
The parameter has now been changed to 7, to show all the files modified in the past week. Since all of these files were created this week, they all show up.
4. -iname
This option allows one to perform a case-insensitive search
Example 1:
```
$ find ./technical/911report -iname "*CHAPTER*"
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
```
Even though the search term CHAPTER was capitalized, all of the results containing chapter were returned as well.
Example 2:
```
$ find ./technical/government/Post_Rate_Comm -iname "*cohenetal*"
./technical/government/Post_Rate_Comm/COHENETAL_comparison.txt
./technical/government/Post_Rate_Comm/Cohenetal_Cost_Function.txt
./technical/government/Post_Rate_Comm/Cohenetal_CreamSkimming.txt
./technical/government/Post_Rate_Comm/Cohenetal_DeliveryCost.txt
./technical/government/Post_Rate_Comm/cohenetal_RuralDelivery.txt
./technical/government/Post_Rate_Comm/CoHeNeTaL_Scale.txt
```
Here, the word cohenetal has been replaced with a variety of cases, but they are all returned due to the option.

For each one, I used the source: https://www.redhat.com/sysadmin/linux-find-command
