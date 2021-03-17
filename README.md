# interviewquestionandanswer
Top 50 programming interview questions

1.) How do you find the missing number in a given integer array of 1 to 100?

https://www.geeksforgeeks.org/find-the-missing-number/

You are given a list of n-1 integers and these integers are in the range of 1 to n. There are no duplicates in the list. One of the integers is missing in the list. Write an efficient code to find the missing integer.
Example: 

Input: arr[] = {1, 2, 4, 6, 3, 7, 8}
Output: 5
Explanation: The missing number from 1 to 8 is 5

Input: arr[] = {1, 2, 3, 5}
Output: 4
Explanation: The missing number from 1 to 5 is 4
Recommended: Please solve it on “PRACTICE ” first, before moving on to the solution.
Method 1: This method uses the technique of the summation formula. 

Approach: The length of the array is n-1. So the sum of all n elements, i.e sum of numbers from 1 to n can be calculated using the formula n*(n+1)/2. Now find the sum of all the elements in the array and subtract it from the sum of first n natural numbers, it will be the value of the missing element.
Algorithm: 
Calculate the sum of first n natural numbers as sumtotal= n*(n+1)/2
Create a variable sum to store the sum of array elements.
Traverse the array from start to end.
Update the value of sum as sum = sum + array[i]
Print the missing number as sumtotal – sum
Implementation:

#include <bits/stdc++.h>
using namespace std;
 
// Function to get the missing number
int getMissingNo(int a[], int n)
{
 
    int total = (n + 1) * (n + 2) / 2;
    for (int i = 0; i < n; i++)
        total -= a[i];
    return total;
}
 
// Driver Code
int main()
{
    int arr[] = { 1, 2, 4, 5, 6 };
    int n = sizeof(arr) / sizeof(arr[0]);
    int miss = getMissingNo(arr, n);
    cout << miss;
}
Output: 
3
 

Complexity Analysis: 
Time Complexity: O(n). 
Only one traversal of the array is needed.
Space Complexity: O(1). 
No extra space is needed
Modification for Overflow  

Approach: The approach remains the same but there can be overflow if n is large. In order to avoid integer overflow, pick one number from known numbers and subtract one number from given numbers. This way there won’t have Integer Overflow ever.
Algorithm: 
Create a variable sum = 1 to which will store the missing number and a counter c = 2.
Traverse the array from start to end.
Update the value of sum as sum = sum – array[i] + c and update c as c++.
Print the missing number as a sum.

#include <bits/stdc++.h>
using namespace std;
 
// a represents the array
// n : Number of elements in array a
int getMissingNo(int a[], int n) 
{ 
    int i, total=1; 
     
    for ( i = 2; i<= (n+1); i++)
    {
        total+=i;
        total -= a[i-2];
    }
    return total; 
} 
 
//Driver Program
int main() {
    int arr[] = {1, 2, 3, 5};
    cout<<getMissingNo(arr,sizeof(arr)/sizeof(arr[0]));
    return 0;
}
 
//This code is contributed by Ankur Goel
Output: 


4
 

Complexity Analysis: 
Time Complexity: O(n). 
Only one traversal of the array is needed.
Space Complexity:O(1). 
No extra space is needed
Thanks to Sahil Rally for suggesting this improvement.
Method 2: This method uses the technique of XOR to solve the problem.  

Approach: 
XOR has certain properties 
Assume a1 ^ a2 ^ a3 ^ …^ an = a and a1 ^ a2 ^ a3 ^ …^ an-1 = b
Then a ^ b = an
Algorithm: 
Create two variables a = 0 and b = 0
Run a loop from 1 to n with i as counter.
For every index update a as a = a ^ i
Now traverse the array from start to end.
For every index update b as b = b ^ array[i]
Print the missing number as a ^ b.
Implementation:

#include <bits/stdc++.h>
using namespace std;
 
// Function to get the missing number
int getMissingNo(int a[], int n)
{
    // For xor of all the elements in array
    int x1 = a[0];
 
    // For xor of all the elements from 1 to n+1
    int x2 = 1;
 
    for (int i = 1; i < n; i++)
        x1 = x1 ^ a[i];
 
    for (int i = 2; i <= n + 1; i++)
        x2 = x2 ^ i;
 
    return (x1 ^ x2);
}
 
// Driver Code
int main()
{
    int arr[] = { 1, 2, 4, 5, 6 };
    int n = sizeof(arr) / sizeof(arr[0]);
    int miss = getMissingNo(arr, n);
    cout << miss;
}
Output: 
3
 

Complexity Analysis: 
Time Complexity: O(n). 
Only one traversal of the array is needed.
Space Complexity: O(1). 
No extra space is needed.
Method 3: This method will work only in python. 
Approach: 
Take the sum of all elements in the array and subtract that from the sum of n+1 elements. For Eg: 
If my elements are li=[1,2,4,5] then take the sum of all elements in li and subtract that from the sum of len(li)+1 elements. The following code shows the demonstration. 


# Python3 program to find
# the mising Number
# getMissingNo takes list as argument 
def getMissingNo(a, n):
    n_elements_sum=n*(n+1)//2
    return n_elements_sum-sum(a)
 
 
# Driver program to test above function
if __name__=='__main__':
 
    a = [1, 2, 4, 5, 6]
    n = len(a)+1
    miss = getMissingNo(a, n) 
    print(miss)
Output:

3
