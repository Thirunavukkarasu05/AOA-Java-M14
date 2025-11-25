
# EX 4E Longest Increasing Subsequence - Dynamic Programming.
## DATE: 25/10/2025
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return the length of the longest strictly increasing subsequence.
Example 1:
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
## Algorithm

1. **Input:**

   * Read the integer `n` (size of array).
   * Read `n` integers into the array `nums`.

2. **Initialization:**

   * Create an array `dp[n]`, where `dp[i]` stores the **length of the longest increasing subsequence (LIS)** ending at index `i`.
   * Initialize all values of `dp` to `1`, since each element is an LIS of length `1` by itself.
   * Initialize `maxLen = 1` to keep track of the overall maximum LIS length.

3. **Dynamic Programming Logic:**

   * For each element `nums[i]` (from index `1` to `n-1`):

     * Compare it with all previous elements `nums[j]` (where `j < i`).
     * If `nums[i] > nums[j]`, it means we can extend the subsequence ending at `j`.
       → Update `dp[i] = max(dp[i], dp[j] + 1)`
   * After each iteration, update `maxLen = max(maxLen, dp[i])`.

4. **Output:**

   * Print `maxLen`, which represents the **length of the longest increasing subsequence**.
 

## Program:
```
/*

Developed by: 
# EX 2A Assign Cookies using Greedy Algorithm. 
## DATE: 01-09-2025
## AIM:
To Write a Java program for the following Constraints.
Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximise the number of your content children and output the maximum number.

## Algorithm
1. Start  
2. Read the number of children `n` and input their greed factors into array `g`.  
3. Read the number of cookies `m` and input their sizes into array `s`.  
4. Sort both arrays `g` (children’s greed) and `s` (cookie sizes) in ascending order.  
5. Initialize three variables:  
   - `i = 0` → pointer for children  
   - `j = 0` → pointer for cookies  
   - `count = 0` → to count satisfied children  
6. While both `i < g.length` and `j < s.length`:  
   - If `s[j] >= g[i]`, assign the cookie to the child: increment both `i` and `j`, and increment `count`.  
   - Else, increment `j` to check the next cookie.  
7. When the loop ends, `count` holds the maximum number of satisfied children.  
8. Print the value of `count`.  
9. End  
   

## Program:
```
/*
Developed by: Thirunavukkarasu P
Register Number:  212222040173
*/

import java.util.*;

public class AssignCookies {

    public static int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        
        int i = 0;
        int j = 0;
        int count = 0;
        
        while (i < g.length && j < s.length) {
            if (s[j] >= g[i]) {
                count++;
                i++;
                j++;
            } else {
                j++;
            }
        }
        
        return count;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int n = sc.nextInt();
        int[] g = new int[n];
        for (int i = 0; i < n; i++) g[i] = sc.nextInt();
        
        int m = sc.nextInt();
        int[] s = new int[m];
        for (int i = 0; i < m; i++) s[i] = sc.nextInt();
        
        System.out.println(findContentChildren(g, s));
    }
}

```

## Output:

<img width="649" height="469" alt="image" src="https://github.com/user-attachments/assets/7c99b307-ae12-415e-b466-f1d82522c440" />


## Result:
The program successfully implemented and the expected output is verified.. 

Register Number:  212222220031
*/
import java.util.*;

public class LongestIncreasingSubsequence {

    public static int lengthOfLIS(int[] nums) {
        if (nums == null || nums.length == 0) return 0;

        int n = nums.length;
        int[] dp = new int[n];  // dp[i] = length of LIS ending at nums[i]
        Arrays.fill(dp, 1);     // Each element is a LIS of length 1 by itself

        int maxLen = 1;

        for (int i = 1; i < n; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            maxLen = Math.max(maxLen, dp[i]);
        }

        return maxLen;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }

        int result = lengthOfLIS(nums);
        System.out.println("Length of Longest Increasing Subsequence: " + result);

        scanner.close();
    }
}

```

## Output:
<img width="812" height="257" alt="image" src="https://github.com/user-attachments/assets/520c0acf-b436-422b-9aff-b9e07ce4377b" />



## Result:
The program successfully implemented and the expected output is verified.
