# [Two Sum](https://leetcode.com/problems/two-sum/)


## Brute Force (Linear Search)

### Code
```Java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for(int i=0;i<nums.length-1;i++){
            for(int ii=i+1;ii<nums.length;ii++){
                int sum = nums[i] + nums[ii];
                if(target==sum)
                    return new int[] {i,ii};
            }
        }
        return null;
    }
}    
```
### Approach
1. Iterate through the array with a nested loop.
2. Check if the the current element and any folloing subsequent element equals to the target.
3. If found return the indexes.

#### Space Complexity - O(1)

#### Time Complexity - 0(n<sup>2</sup>)
