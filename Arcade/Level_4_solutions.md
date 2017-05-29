## Test 1 alternatingSums

Several people are standing in a row and need to be divided into two teams. The first person goes into team 1, the second goes into team 2, the third goes into team 1 again, the fourth into team 2, and so on.

You are given an array of positive integers - the weights of the people. Return an array of two integers, where the first element is the total weight of team 1, and the second element is the total weight of team 2 after the division is complete.

Example

For a = [50, 60, 60, 45, 70], the output should be
alternatingSums(a) = [180, 105].

Input/Output

[time limit] 4000ms (py)
[input] array.integer a

Guaranteed constraints:
1 ≤ a.length ≤ 10,
45 ≤ a[i] ≤ 100.

[output] array.integer

```python
def alternatingSums(a):
    sum_weight = [0, 0]
    for n in range(0, len(a), 2):
        sum_weight[0] += a[n]
    if len(a)>1 :
        for n in range(1, len(a), 2):
            sum_weight[1] += a[n]
    return sum_weight
```

## Test 2 addBorder
Given a rectangular matrix of characters, add a border of asterisks(*) to it.

Example

For

picture = ["abc",
           "ded"]
the output should be

addBorder(picture) = ["*****",
                      "*abc*",
                      "*ded*",
                      "*****"]
Input/Output

[time limit] 4000ms (py)
[input] array.string picture

A non-empty array of non-empty equal-length strings.

Guaranteed constraints:
1 ≤ picture.length ≤ 5,
1 ≤ picture[i].length ≤ 5.

[output] array.string

The same matrix of characters, framed with a border of asterisks of width 1.

```python
def addBorder(picture):
    w = len(picture[0])
    h = len(picture)
    new_picture = ["*"*(w+2)]*(h+2)
    if w >0:
        for n_h in range(h):
            new_picture[n_h+1] = "*" + picture[n_h] + "*"
    return new_picture
```

## Test 3 areSimilar
Two arrays are called similar if one can be obtained from another by swapping at most one pair of elements in one of the arrays.

Given two arrays, check whether they are similar.

Example

For A = [1, 2, 3] and B = [1, 2, 3], the output should be
areSimilar(A, B) = true.

The arrays are equal, no need to swap any elements.

For A = [1, 2, 3] and B = [2, 1, 3], the output should be
areSimilar(A, B) = true.

We can obtain B from A by swapping 2 and 1 in B.

For A = [1, 2, 2] and B = [2, 1, 1], the output should be
areSimilar(A, B) = false.

Any swap of any two elements either in A or in B won't make A and B equal.

Input/Output

[time limit] 4000ms (py)
[input] array.integer A

Array of integers.

Guaranteed constraints:
3 ≤ A.length ≤ 105,
1 ≤ A[i] ≤ 1000.

[input] array.integer B

Array of integers of the same length as A.

Guaranteed constraints:
B.length = A.length,
1 ≤ B[i] ≤ 1000.

[output] boolean

true if A and B are similar, false otherwise.

```python
def areSimilar(A, B):
    diff_pair = [ [a,b] for a,b in zip(A,B) if a!=b]
    if len(diff_pair) == 0:
        return True
    elif len(diff_pair) ==2:
        if diff_pair[0][1] == diff_pair[1][0] and diff_pair[0][0] == diff_pair[1][1]:
            return True
        else:
            return False
    else:
        return False
```

## Test 4 arrayChange
You are given an array of integers. On each move you are allowed to increase exactly one of its element by one. Find the minimal number of moves required to obtain a strictly increasing sequence from the input.

Example

For inputArray = [1, 1, 1], the output should be
arrayChange(inputArray) = 3.

Input/Output

[time limit] 4000ms (py)
[input] array.integer inputArray

Guaranteed constraints:
3 ≤ inputArray.length ≤ 105,
-105 ≤ inputArray[i] ≤ 105.

[output] integer

The minimal number of moves needed to obtain a strictly increasing sequence from inputArray.
It's guaranteed that for the given test cases the answer always fits signed 32-bit integer type.

```python
def arrayChange(inputArray):
    sumChange = 0
    for n in range(len(inputArray)-1):
        if inputArray[n+1] < inputArray[n] + 1:
            sumChange += (inputArray[n] + 1 - inputArray[n+1])
            inputArray[n+1] = inputArray[n] + 1
    return sumChange
```

## Test 5 palindromeRearranging
Given a string, find out if its characters can be rearranged to form a palindrome.

Example

For inputString = "aabb", the output should be
palindromeRearranging(inputString) = true.

We can rearrange "aabb" to make "abba", which is a palindrome.

Input/Output

[time limit] 4000ms (py)
[input] string inputString

A string consisting of lowercase English letters.

Guaranteed constraints:
4 ≤ inputString.length ≤ 50.

[output] boolean

true if the characters of the inputString can be rearranged to form a palindrome, false otherwise.

```python
def palindromeRearranging(inputString):
    chars = "abcdefghijklmnopqrstuvwxyz"
    count = [True for char in chars if inputString.count(char) % 2 == 1]
    return len(count) < 2
```
