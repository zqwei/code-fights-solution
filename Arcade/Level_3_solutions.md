## Test 1 allLongestStrings

Given an array of strings, return another array containing all of its longest strings.

**Example**

For inputArray = ["aba", "aa", "ad", "vcd", "aba"], the output should be allLongestStrings(inputArray) = ["aba", "vcd", "aba"].

**Input/Output**

* [time limit] 4000ms (py)
* [input] array.string inputArray: A non-empty array. Guaranteed constraints: 1 ≤ inputArray.length ≤ 10, 1 ≤ inputArray[i].length ≤ 10.
* [output] array.string: Array of the longest strings, stored in the same order as in the inputArray.

```python
def allLongestStrings(inputArray):
    lenString = [len(i_string) for i_string in inputArray]
    max_len = max(lenString)
    ind = [i for i in range(len(lenString)) if lenString[i]==max_len]
    return [inputArray[nind] for nind in ind]
```    

## Test 2 commonCharacterCount
Given two strings, find the number of common characters between them.

**Example**

For s1 = "aabcc" and s2 = "adcaa", the output should be
commonCharacterCount(s1, s2) = 3. Strings have 3 common characters - 2 "a"s and 1 "c".

**Input/Output**

* [time limit] 4000ms (py)
* [input] string s1: A string consisting of lowercase latin letters a-z. Guaranteed constraints: 3 ≤ s1.length ≤ 15.
* [input] string s2： A string consisting of lowercase latin letters a-z. Guaranteed constraints: 4 ≤ s2.length ≤ 15.
* [output] integer

```python
def commonCharacterCount(s1, s2):
    n_common = 0
    for n_s1 in s1:
        if n_s1 in s2:
            n_common += 1
            s2 = s2.replace(n_s1, "", 1)
    return n_common
```

## Test 3 isLucky

Ticket numbers usually consist of an even number of digits. A ticket number is considered lucky if the sum of the first half of the digits is equal to the sum of the second half. Given a ticket number n, determine if it's lucky or not.

**Example**

For n = 1230, the output should be isLucky(n) = true;
For n = 239017, the output should be isLucky(n) = false.

**Input/Output**

* [time limit] 4000ms (py)
* [input] integer n: A ticket number represented as a positive integer with an even number of digits. Guaranteed constraints: 10 ≤ n < 106.
* [output] boolean: true if n is a lucky ticket number, false otherwise.

```python
def isLucky(n):
    lst_num = [int(i) for i in str(n)]
    half_len = len(lst_num)/2
    return sum(lst_num[:half_len]) == sum(lst_num[half_len:])
```

## Test 4

Some people are standing in a row in a park. There are trees between them which cannot be moved. Your task is to rearrange the people by their heights in a non-descending order without moving the trees.

**Example**

For a = [-1, 150, 190, 170, -1, -1, 160, 180], the output should be
sortByHeight(a) = [-1, 150, 160, 170, -1, -1, 180, 190].

Input/Output

[time limit] 4000ms (py)
[input] array.integer a

If a[i] = -1, then the ith position is occupied by a tree. Otherwise a[i] is the height of a person standing in the ith position.

Guaranteed constraints:
5 ≤ a.length ≤ 15,
-1 ≤ a[i] ≤ 200.

[output] array.integer

Sorted array a with all the trees untouched.    

```python
def sortByHeight(a):
    untreeIndex = [i for i in range(len(a)) if a[i] != -1]
    untreeA = [i for i in a if i != -1]
    untreeA.sort()
    for n_index, n_A in zip(untreeIndex, untreeA):
        a[n_index] = n_A
    return a
```

## Test 5

You have a string s that consists of English letters, punctuation marks, whitespace characters, and brackets. It is guaranteed that the parentheses in s form a regular bracket sequence. Your task is to reverse the strings contained in each pair of matching parentheses, starting from the innermost pair. The results string should not contain any parentheses.

**Example**

For string s = "a(bc)de", the output should be
reverseParentheses(s) = "acbde".

Input/Output

[time limit] 4000ms (py)
[input] string s

A string consisting of English letters, punctuation marks, whitespace characters and brackets. It is guaranteed that parentheses form a regular bracket sequence.

Constraints:
5 ≤ s.length ≤ 55.

[output] string

```python
def reverseParentheses(s):
    while "(" in s:
        last_ind = [i for i in range(len(s)) if s[i] == ")"]
        last_ind = min(last_ind)
        first_ind = [i for i in range(last_ind) if s[i] == "("]
        first_ind = max(first_ind)
        s = s[:first_ind] + s[last_ind-1:first_ind:-1] + s[last_ind+1:]
    return s
```