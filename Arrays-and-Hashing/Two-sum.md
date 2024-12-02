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

#### Time Complexity - O(n<sup>2</sup>)

## Single Pass Hash Table

### Code
```Java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> TwoSum = new HashMap<>();
        for(int i=0;i<nums.length;i++){
            int diff = target - nums[i];
            if(TwoSum.containsKey(diff))
                return new int[] {TwoSum.get(diff), i};
            TwoSum.put(nums[i],i);
        }
        return null;
    }
}
```
### Approach
1. Iterate through the list
2. Find the complement of each element *target-nums[i]*
3. Check if the complement value is present in the hash table
4. If not add the element and its index in the hash table
5. This apporach of adding elements simultaneously with the search loop avoids return same index values

#### Space Complexity - O(n) We store elements in the hash table

#### Time Complexity - O(n) We iterate through the list once

## Two Pass Hash Table

### Code
```Java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> TwoSum = new HashMap<>();
        for(int i=0;i<nums.length;i++){
            TwoSum.put(nums[i],i);
        }
        for(int i=0;i<nums.length;i++){
            int diff = target - nums[i];
            if(TwoSum.containsKey(diff) && TwoSum.get(diff) != i)
                return new int[] {i, TwoSum.get(diff)};
        }
        return null;
    }
}
```

### Approach
1. Populate the Hash table with the element and its respective index
2. Find the complement of the element and search it in the hash table.
3. Add a condition such that the complement of the element is not the same as the element

#### Space Complexity - O(n) Stores n elements in the hash map

#### Time Complexity - O(2n) = O(n) Both the times iterates through the array once
