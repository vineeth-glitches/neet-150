# [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

## Sorting method

### Code

```Java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);
        for(int i=1;i<nums.length;i++){
            if(nums[i]==nums[i-1])
                return true;
        }
        return false;
    }
}
```

### Approach
1. We sort the array using the *sort*function(Dual-Pivot Quicksort) which uses O(nlog(n)) time.
2. Duplicate elements will be sorted together, hence we compare the adjust to see if its equal
3. If equal we return true else we return false

#### Space Complexity - O(1)
Array.sort for primitive types is O(1), if the array contains objects it will be O(n)

#### Time Complexity - O(n Log n)
The sort function takes O(n log n) and the for loop to iterate through the array takes O(n), combined gives us O(n log n)

## HashSet

### Code
```Java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> uniqNum = new HashSet<Integer>();
        for(int i: nums){
            if(uniqNum.contains(i))
                return true;
            uniqNum.add(i);
        }
        return false;
    }
}
```

### Approach
1. HashSet is unique and doesnt store duplicate values.
2. We check and constantly add elements in the hashset
3. If in the process of iteration, we encounter that the element is already present in the hashset we return true.

#### Space Complexity - O(n)
The space required for hashset is proportional to the number of unique elements in the array, hence O(n)

#### Time Complexity - O(n)
HashSet operations like contains(i) and add(i) is O(n). Iterating through the array is O(n).
