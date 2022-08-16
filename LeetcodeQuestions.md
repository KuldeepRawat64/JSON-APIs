
# Leetcode Questions
---

## Easy

### Arrays

#### Merge two sorted arrays
       
##### Algorithm: 
    -  MERGE_SORT(arr, beg, end)  
    -   
    - if beg < end  
    - set mid = (beg + end)/2  
    - MERGE_SORT(arr, beg, mid)  
    - MERGE_SORT(arr, mid + 1, end)  
    - MERGE (arr, beg, mid, end)  
    - end of if  
    -   
    - END MERGE_SORT  

##### Method (O(n1 + n2) Time and O(n1 + n2) Extra Space)      The idea is to use Merge function of Merge sort. 
     Create an array arr3[] of size n1 + n2.
     Simultaneously traverse arr1[] and arr2[]. 
    * Pick smaller of current elements in arr1[] and arr2[], copy this smaller element to next position in arr3[] and move ahead in arr3[] and the array whose element is picked.
    If there are remaining elements in arr1[] or arr2[], copy them also in arr3[].

##### Code (Java):
```
// Java program to merge two sorted arrays
import java.util.*;
import java.lang.*;
import java.io.*;

class MergeTwoSorted
{
	// Merge arr1[0..n1-1] and arr2[0..n2-1]
	// into arr3[0..n1+n2-1]
	public static void mergeArrays(int[] arr1, int[] arr2, int n1,
								int n2, int[] arr3)
	{
		int i = 0, j = 0, k = 0;
	
		// Traverse both array
		while (i<n1 && j <n2)
		{
			// Check if current element of first
			// array is smaller than current element
			// of second array. If yes, store first
			// array element and increment first array
			// index. Otherwise do same with second array
			if (arr1[i] < arr2[j])
				arr3[k++] = arr1[i++];
			else
				arr3[k++] = arr2[j++];
		}
	
		// Store remaining elements of first array
		while (i < n1)
			arr3[k++] = arr1[i++];
	
		// Store remaining elements of second array
		while (j < n2)
			arr3[k++] = arr2[j++];
	}
	
	public static void main (String[] args)
	{
		int[] arr1 = {1, 3, 5, 7};
		int n1 = arr1.length;
	
		int[] arr2 = {2, 4, 6, 8};
		int n2 = arr2.length;
	
		int[] arr3 = new int[n1+n2];
		
		mergeArrays(arr1, arr2, n1, n2, arr3);
	
		System.out.println("Array after merging");
		for (int i=0; i < n1+n2; i++)
			System.out.print(arr3[i] + " ");
	}
}

/* This code is contributed by Mr. Somesh Awasthi */

 ```
       

##### Code (Dart):
```
void main(){
List<int> arr1 = [1,3,5,7];
int n1 = arr1.length;
List<int> arr2 = [2,4,6,8];
int n2 = arr2.length;
List<int> arr3 = List<int>.filled(n1+n2, 0);
mergeTwoSortedArrays(arr1, n1, arr2, n2, arr3);
print(arr3);
}
 
 void mergeTwoSortedArrays(List<int> arr1, int n1, List<int> arr2, int n2, List<int> arr3){
 int i = 0; int j = 0; int k = 0;
 
 while( i< n1 && j < n2)
 }
```




#### Remove duplicates from sorted array

##### Algorithm : 
**Method 1:** (Using extra space) 

1.  Create an auxiliary array temp\[\] to store unique elements.
2.  Traverse input array and one by one copy unique elements of arr\[\] to temp\[\]. Also keep track of count of unique elements. Let this count be **j**.
3.  Copy **j** elements from temp\[\] to arr\[\] and return j


#####    Code (Java):
```
// simple java program to remove duplicates

class Main {
	// Function to remove duplicate elements This function
	// returns new size of modified array.
	static int removeDuplicates(int arr[], int n)
	{
		// Return, if array is empty or contains a single
		// element
		if (n == 0 || n == 1)
			return n;

		int[] temp = new int[n];

		// Start traversing elements
		int j = 0;
		for (int i = 0; i < n - 1; i++)
			// If current element is not equal to next
			// element then store that current element
			if (arr[i] != arr[i + 1])
				temp[j++] = arr[i];

		// Store the last element as whether it is unique or
		// repeated, it hasn't stored previously
		temp[j++] = arr[n - 1];

		// Modify original array
		for (int i = 0; i < j; i++)
			arr[i] = temp[i];

		return j;
	}

	public static void main(String[] args)
	{
		int arr[] = { 1, 2, 2, 3, 4, 4, 4, 5, 5 };
		int n = arr.length;

		n = removeDuplicates(arr, n);

		// Print updated array
		for (int i = 0; i < n; i++)
			System.out.print(arr[i] + " ");
	}
}

// This code is contributed by Aditya Kumar (adityakumar129)

```

#####    Code (Dart):
```
void maain(){
List<int> nums = [1,2,2,3,4,5];
int n = nums.length;
n = removeDuplicates(nums, n);
for(int i = 0; i< n; i++){
print(nums[i]);
}
}

int removeDuplicates(List<int> nums, int n){
int j = 0;
for(int i=0; i < n -1; i++){
if(nums[i] != nums[ i + 1]){
nums[j++] = nums[i];
}
}
nums[j++] = nums[n - 1];
return j;
}
```


#### Two sum and print the pair if exists

#####   Algorithm : 
**Method:** Using simple logic by calculating the array’s elements themselves.

#####   Code (Java):
```
// Java program to check if there exists a pair
// in array whose sum results in x.
class GFG{

// Function to find and print pair
static boolean chkPair(int A[], int size, int x) {
	for (int i = 0; i < (size - 1); i++) {
		for (int j = (i + 1); j < size; j++) {
			if (A[i] + A[j] == x) {
				System.out.println("Pair with a given sum " + x +
									" is (" + A[i] + ", " + A[j] + ")");

				return true;
			}
		}
	}

	return false;
}

public static void main(String [] args) {
	
	int A[] = {0, -1, 2, -3, 1};
	int x = -2;
	int size = A.length;

	if (chkPair(A, size, x)) {
		System.out.println("Valid pair exists");
	}
	else {
		System.out.println("No valid pair exists for " + x );
	}
}
}

// This code is contributed by umadevi9616

```

#####   Code (Dart):
```
// Java program to check if there exists a pair
// in array whose sum results in x.

// Function to find and print pair
bool chkPair(List<int> A, int size, int x) {
  for (int i = 0; i < (size - 1); i++) {
    for (int j = (i + 1); j < size; j++) {
      if (A[i] + A[j] == x) {
        print("${A[i]} ${A[j]}");
        return true;
      }
    }
  }

  return false;
}

void main() {
  List<int> A = [0, -1, 2, -3, 1];
  int x = -2;
  int size = A.length;

  if (chkPair(A, size, x)) {
    print("Valid pair exists");
  } else {
    print("No valid pair exists for   $x ");
  }
}

```

#### Two sum and print the indices of the pair if exists

#####   Algorithm : 


#####   Code (Java):
```
import java.util.HashMap;
import java.util.Map;

public class Main {

    public static int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> visitedNums = new HashMap<>();
        for(int i = 0; i < nums.length; i++){
            int delta = target - nums[i];
            if(visitedNums.containsKey(delta)){
                return new int[] {visitedNums.get(delta), i};


            }
            visitedNums.put(nums[i], i);

        }
        return new int[]{-1,-1};
    }
    public static void main(String[] args) {
        int[] nums = new int[]{3,2,4};
        int target = 6;
        int[] indices = twoSum(nums,target);
        System.out.println(indices[0] + " "+indices[1]);

    }
}
```

#####   Code (Dart):
```
List<int> twoSum(List<int> nums, int target) {
  var visitedNums = {};
  List<int> indices = [];
  for (int number in nums) {
    if (visitedNums.containsKey(number)) {
      indices.add(visitedNums[number]);
      indices.add(nums.indexOf(number));

      return indices;
    }
    visitedNums[target - number] = nums.indexOf(number);
  }
  return indices;
}

void main() {
  List<int> nums = [4, 2, 3];
  int target = 6;
  List<int> indices = [];
  indices = twoSum(nums, target);
  if (indices.length == 2) {
    print("${indices[0]} ${indices[1]}");
  }
}

```


