# BiWeekly Contest Solutions - 126

## Problem 1: Find the Sum of Encrypted Integers

### Problem Statement
Given an integer array `nums` containing positive integers, we define a function `encrypt` such that `encrypt(x)` replaces every digit in `x` with the largest digit in `x`. The task is to return the sum of encrypted elements.

### Constraints
- 1 <= `nums.length` <= 50
- 1 <= `nums[i]` <= 1000

### Approach
The approach is to convert each number into a string and sort the characters in the string. The largest digit will be at the end of the sorted string. We then create a new string with the same length as the original number but filled with the largest digit. This new string is then converted back to an integer and added to the sum.

```java
class Solution {
    public int encrypt(int num){
        String str = Integer.toString(num);
        char[] arr = str.toCharArray();
        Arrays.sort(arr);
        StringBuilder sb = new StringBuilder();
        char n = arr[arr.length -1];
        for(int i = 0 ; i < str.length();i++){
            sb.append(n);
        }
        String result = sb.toString();
        int number = Integer.parseInt(result);
        return number;
    }

    public int sumOfEncryptedInt(int[] nums) {
        int sum  = 0;
        for(int i = 0 ; i < nums.length;i++){
            sum += encrypt(nums[i]);
        }
        return sum;
    }
}
```
## Problem 2: Find the Sum of the Power of All Subsequences

### Problem Statement
Given an integer array nums of length n and a positive integer k, the power of an array of integers is defined as the number of subsequences with their sum equal to k. The task is to return the sum of power of all subsequences of nums. Since the answer may be very large, return it modulo 10^9 + 7.
### Constraints
- 1 <= n <= 100
- 1 <= nums[i] <= 10^4
- 1 <= k <= 100

### Approach
The approach is to use dynamic programming to keep track of the number of subsequences with sum equal to k. We initialize an array arr of size k+1 with arr[0] = 1. For each number in nums, we iterate from k to num and update arr[i] as arr[i] + arr[i - num]. The answer will be arr[k].

```bash
class Solution {
    public int sumOfPower(int[] nums, int k) {
        int MOD = 1000000007;
        int[] arr = new int[k + 1];
        arr[0] = 1; 
        for (int num : nums) {
            for (int i = k; i >= num; i--) {
                arr[i] = (arr[i] + arr[i - num]) % MOD;
            }
        }
        return arr[k];
    }
}
```
