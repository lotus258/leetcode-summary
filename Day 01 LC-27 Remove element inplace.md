https://leetcode.com/problems/remove-element/

Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.

### Brute force:

```
class Solution {
    public int removeElement(int[] nums, int val) {
        //brute force
        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] ==  val && (count + i < nums.length)) {
                for (int j = i; j < nums.length - 1; j++) {
                    nums[j] = nums[j + 1];
                }
                count++;
            }


//特别注意这一步要再次判断左移后同一位置是否还是等于target. 这里也可以直接i--进行再一次判断。
            if (nums[i] == val && (count + i < nums.length)) {
                i--;
            }
        }
        return nums.length - count;
    }
}
```


### Two pointer:

```
class Solution {
    public int removeElement(int[] nums, int val) {
        //two pointers
        int slow = 0;
        for (int i = 0; i < nums.length; i++) {
            nums[slow] = nums[i];
            if (nums[i] != val) {
                slow++;
            }
        }
        return slow;
    }
}
```
