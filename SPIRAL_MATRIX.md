## SPIRAL MATRIX

Given an m x n matrix, return all elements of the matrix in spiral order.

 

Example 1:


Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [1,2,3,6,9,8,7,4,5]
Example 2:


Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
 

Constraints:

m == matrix.length
n == matrix[i].length
1 <= m, n <= 10
-100 <= matrix[i][j] <= 100


## solution

```js
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var spiralOrder = function(matrix) {
   let m = matrix.length;
   let n = matrix[0].length;
    let totalIteration = m*n;
    let down = 0;
    let right = 1;
    let row = 0;
    let column = 0;
    let result = [];
    while(totalIteration--) {
        // console.log(`[${row}][${column}] = ${matrix[row][column]}`)
        if(!isNaN(matrix[row][column])) {
            result.push(matrix[row][column]);
            matrix[row][column] = NaN;
        }
        if(down == 0 && right == 1) {
            // console.log("right");
            if(column+ right == n || isNaN(matrix[row][column+right])) {
                right = 0;
                down = 1;
            }
        } else if(down == 1 && right == 0) {
            if(row + down == m || isNaN(matrix[row + down][column])) {
                right = -1;
                down = 0;
            }
        }
        else if(down == 0 && right == -1) {
            if(column + right == -1 || isNaN(matrix[row][column + right])) {
                right = 0;
                down = -1;
            }
        }
        else if(row + down == -1 || isNaN(matrix[row + down][column])) {
            right = 1;
            down = 0;
        }
        
        
        row = row + down;
        column = column + right;
    }
    return result;
   
};
```
