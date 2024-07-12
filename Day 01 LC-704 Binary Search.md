https://leetcode.com/problems/binary-search/description/

Leetcode 704 Binary search

1. Include both left and right boundary
```
class Solution {
    public int search(int[] nums, int target) {
        if (nums.length == 0 || nums == null) return -1;
        int left = 0;
        int right = nums.length - 1;

        while(left <= right) {
            int mid = left + (right - left)/2;

            if (nums[mid] == target) {
                return mid;
            }

            if (nums[mid] > target) {
                right = mid - 1;
            }

            if (nums[mid] < target) {
                left = mid + 1;
            }
        }
        return -1;
    }
}
```

2. Include left boundary, not include right boundary.
```
class Solution {
    public int search(int[] nums, int target) {
        if (nums.length == 0 || nums == null) return -1;

        int left = 0;
        int right = nums.length;

        while(left < right) {
            int mid = (left + right) / 2;

            if (nums[mid] == target) {
                return mid;
            }

            if (nums[mid] > target) {
                right = mid;
            } else

            if (nums[mid] < target) {
                left = mid + 1;
            }
        }
        return -1;
    }
}
```
3. Recursion
```
class Solution {
    public int search(int[] nums, int target) {
        if (nums.length == 0 || nums == null) return -1;
        int left = 0;
        int right = nums.length - 1;

        return helper(nums, left, right, target);
    }

    public int helper(int[] nums, int left, int right, int target) {
        //recursion exit 1; this should be checked first
        if (left > right) return -1;

        //recusion exit 2; return when target found
        int mid = left + (right - left) / 2;
        if (nums[mid] == target) return mid;

        if (nums[mid] > target) {
            return helper(nums, left, mid - 1, target);
        } else {
            return helper(nums, mid + 1, right, target);
        }
    }
}
```
