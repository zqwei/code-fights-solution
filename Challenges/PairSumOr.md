Given an array of non-negative integers arr, you task is to calculate the sum of bitwise OR operations (arr[i] | arr[j]) for all the pairs of integers in it.

Example

For arr = [1, 2, 3], the output should be
pairSumOr(arr) = 9.

arr[0] | arr[1] = 1 | 2 = 12 | 102 = 112 = 3
arr[0] | arr[2] = 1 | 3 = 12 | 112 = 112 = 3
arr[1] | arr[2] = 2 | 3 = 102 | 112 = 112 = 3
Thus, the answer is 3 + 3 + 3 = 9.

For arr = [1, 2, 3, 4, 5], the output should be
pairSumOr(arr) = 51.

The answer can be obtained as follows:

(1 | 2) + (1 | 3) + (1 | 4) + (1 | 5) +
          (2 | 3) + (2 | 4) + (2 | 5) +
          (3 | 4) + (3 | 5) +
          (4 | 5)
        = 51
Input/Output

[time limit] 4000ms (py)
[input] array.integer arr

Guaranteed constraints:
0 ≤ arr.length ≤ 5 · 105,
0 ≤ arr[i] < 231.

[output] integer64

The answer is guaranteed to be less than 250.

```python
def pairSumOr(arr):
    sum = 0
    len_arr = len(arr)
    if len_arr > 0:
        len_bit = len(bin(max(arr))) - 1
        for i in range(len_bit):
            k = 0
            for j in range(len_arr):
                if not (arr[j] & (1<<i)):
                    k += 1
            if k < len_arr:
                sum += (1<<i) * (len_arr*(len_arr-1)/2 - k*(k-1)/2)
    return int(sum)
```
