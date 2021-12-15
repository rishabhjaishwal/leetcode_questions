## problem

Given an array of integers nums and an integer target, return indices of the two sequencial numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]
 

Constraints:

2 <= nums.length <= 104
-109 <= nums[i] <= 109
-109 <= target <= 109
Only one valid answer exists.
 

Follow-up: Can you come up with an algorithm that is less than O(n2) time complexity?

## output 

```js
var twoSum = function(nums, target) {
    const length = nums.length;
    let sumArray = [];
    let sum = 0;
   for(let i = 0; i < length; i++) {
        if(nums[i] <= target ) {
            if((sum + nums[i]) > target) {
                sum = sum - sumArray[0];
                sumArray.shift();
            }
            sumArray.push(i);
            sum = sum + nums[i];
            if(sum == target) {
                break;
            }
        } else {
            sumArray = [];
            sum = 0;
        }
   }
    return sumArray;
};
```
