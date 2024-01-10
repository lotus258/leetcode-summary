https://leetcode.con/problems/remove-element/

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
