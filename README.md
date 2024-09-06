Minimum number of merge operations required to make an array palindrome in C++
Here, in this page we will discuss the program to find Minimum number of merge operations required to make an array palindrome in C++ programming language. We are given with an array and we need to print an integer value denoting the number of operations required.

Minimum number of merge operations
Method 1 :
Declare a variable say, count=0, that will count the required merging operation.
Take two variables, i=0, and j=n-1.
Now, run a loop till i<j, inside loop check if (arr[i]==arr[j]), then increase the value of i by 1 and decrease the value of j by 1.
Else if (arr[i]>arr[j]), then set arr[j-1] = arr[j-1]+arr[j] and decrease the value of j and increase the value of count by 1.
Else set, arr[i+1] = arr[i]+arr[i+1] and increase the value of i and count by 1.
After the traversal print the value of count.
Time and Space Complexity :
Time-Complexity : O(n)
Space-Complexity : O(1)
Number of merge operations
Code in C++
Run
#include<bits/stdc++.h>
using namespace std;

int main(){

int arr[] = {1, 4, 5, 9, 1};
int n = sizeof(arr)/sizeof(arr[0]), count = 0;

int i=0, j=n-1;

while(i< j){ 
    if(arr[i]==arr[j])
    { 
        i++; 
        j--; 
        
    } 
    else if(arr[i]>arr[j]){
        arr[j-1] = arr[j]+arr[j-1];
        j--;
        count++;
    }
else{
    arr[i+1] = arr[i]+arr[i+1];
    i++;
    count++;
    }
}

cout<< "Required Minimum Operations : "<< count;
}
Output :
Required Minimum Operations : 1
Related Pages
Given an array which consists of only 0, 1 and 2

Move all the negative elements to one side of the array

Minimum no. of Jumps to reach the end of an array 

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Method 2 (Using Recursion) :
Create a recursive function say, fun() pass arr and two values 0 and n-1.
In the fun(), return 0, if(i==j or i>j)
Otherwise, check if (arr[i]==arr[j]), then return(1+fun(arr, i+1, j-1))
Else check if (arr[i]>arr[j]), then set arr[j-1] = arr[j-1]+arr[j] and return(1+fun(arr, i, j-1))
Else set, arr[i+1] = arr[i]+arr[i+1] and return(1+fun(arr, i+1, j)).
Time and Space Complexity :
Time-Complexity : O(n)
Space-Complexity : O(1)
Code in C++
Run
#include<bits/stdc++.h>
using namespace std;

int fun(int arr[], int i, int j){

      if( i==j or i>j )
         return 0;

     if(arr[i]==arr[j])
         return fun(arr, i+1, j-1);

     else if(arr[i]>arr[j]){
          arr[j-1] = arr[j]+arr[j-1];
          return (1+fun( arr, i, j-1));
     }
     else{
          arr[i+1] = arr[i]+arr[i+1];
          return (1+fun( arr, i+1, j));
     }

}

int main(){

int arr[] = {1, 4, 5, 9, 1};
int n = sizeof(arr)/sizeof(arr[0]);

cout<<"Required Minimum Operations : "<< fun(arr, 0 , n-1);
}
Output :
Required Minimum Operations : 1
