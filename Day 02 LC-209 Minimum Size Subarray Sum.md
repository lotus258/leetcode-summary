https://leetcode.com/problems/minimum-size-subarray-sum/description/

## Brute force to get all the subarrays and select the min size one

Runtime limit exceeded. Runtime is O(n^2) due to nested for loops.

```
class Solution {
    public int minSubArrayLen(int target, int[] nums) {

        //brute force to get all subarray and get the min one.

        int min_len = Integer.MAX_VALUE;

        for (int i = 0; i < nums.length; i++) {
            int local_sum = 0;
            int count = 0;

            for (int j = i; j < nums.length; j++) {
                count++;
                local_sum += nums[j];
                if (local_sum >= target && count < min_len) {
                    min_len = count;
                }
            }
        }
        return min_len == Integer.MAX_VALUE ? 0 : min_len;
    }
}

```
