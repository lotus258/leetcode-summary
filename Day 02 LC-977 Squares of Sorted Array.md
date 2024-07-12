https://leetcode.com/problems/squares-of-a-sorted-array/description/

## Two pointers

The array is sorted so we have to use this feature. Time complexity is O(n).

```
class Solution {
    public int[] sortedSquares(int[] nums) {
        int left = 0;
        int right = nums.length - 1;
        int[] result = new int[nums.length];
        int pointer = nums.length - 1;

        while (left <= right) {
            int left_sqr = nums[left] * nums[left];
            int right_sqr = nums[right] * nums[right];

            if (left_sqr > right_sqr) {
                result[pointer] = left_sqr;
                left++;

            } else {
                result[pointer] = right_sqr;
                right--;
            }

            pointer--;
        }

        return result;
    }
}
```
