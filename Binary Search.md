## problem 
Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
Example 2:

Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1
 

Constraints:

1 <= nums.length <= 104
-104 < nums[i], target < 104
All the integers in nums are unique.
nums is sorted in ascending order.

## answer

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
    const length = nums.length;
    if(!length) {
        return -1;
    } else {
        if(length == 1) {
            if(nums[0] === target) {
                return 0;
            } else {
                return -1;
            }
        }
        
        const mid = Math.ceil(length/2);
        if(nums[mid] === target) {
            return mid;
        } else if(nums[mid] < target) {
                const index = search(nums.splice(mid+1,length), target);
            if(index > -1) {
                return mid + index + 1;
            } else {
                return -1;
            }
            } else if(nums[mid] > target) {
                return search(nums.splice(0, mid), target);
            }
    }
};
```
