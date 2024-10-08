Row with Maximum no. of 1’s in Python
Here on this page, we will learn how to Find a Row with Maximum no. of 1’s in Python Language.

Example :

Input :  matrix  =  [ [ 0, 1, 0, 0 ],
                                 [ 1, 0, 0, 1 ],
                                 [ 1, 1, 1, 1 ],
                                 [ 0, 0, 1, 1 ] ]
Output :  3rd Row
Row with Maximum no. of 1’s in Python

Method Discussed :
Method 1 : Naïve Method
Method 2 : Using Binary Search.
Algorithm ( Method 1 )
In this method we will traverse each row of the matrix,
Find the count of 1’s in each row.
Then compare it with max_count and the index value.
After complete iteration, print the value of the index.
Time and Space Complexity :
Time-Complexity : O(r*c)
Space-Complexity : O(1)
Row with Maximum no. of 1’s
Python Code
Run
Matrix = [[0, 0, 0, 1],
          [0, 1, 1, 1],
          [1, 1, 1, 1],
          [0, 0, 0, 0]]

max_count, row = 0, -1

for i in range(4):

    count = 0
    for j in range(4):
        if Matrix[i][j] == 1:
            count += 1

    if count > max_count:
        max_count = count
        row = i

print("Row with maximum 1's is :", row+1)
Output
Row with maximum 1's is : 3
Algorithm ( Method 2 )
Take a variable to hold the index value of required row, let it be index=-1, and max_count=0, that hold the maximum count of 1.
Now, iterate over each row, and take variable say count=0, to count the number of 1’s in current row.
For, i-th row, use binary search to find the first instance of 1.
Then count = No. of columns – first instance of 1.
Check if count > max_count, then set max_count = count and index=i.
After the iteration of all rows, print the value of the index.
Time and Space Complexity :
Time-Complexity : O(r*log(c))
Space-Complexity : O(1)
Run
def first(arr, low, high):
    
    if high >= low:
        
        mid = low + (high - low) // 2
        if (mid == 0 or arr[mid - 1] == 0) and arr[mid] == 1:
            return mid

        elif arr[mid] == 0:
            return first(arr, (mid + 1), high)

        else:
            return first(arr, low, (mid - 1))

    return -1


Matrix = [[0, 0, 0, 1],
          [0, 1, 1, 1],
          [1, 1, 1, 1],
          [0, 0, 0, 0]]

max_count, row = 0, -1

for i in range(4):

    count = 0
    x = first(Matrix[i], 0, 3)
    if x != -1:
        count = 4 - x
    if count > max_count:
        max_count = count
        row = i

print("Row with maximum 1's is :", row + 1)
Output
Row with maximum 1's is : 3
