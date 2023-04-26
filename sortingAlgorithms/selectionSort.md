# Selection Sort
Selection sort is an unstable sort and may not guarante that similar sorted element stay in the order in which they are inputed.
It has a time complexity of O(n^2): as we need to go through each index in the array comparing it with other number in the array while arranging smallest number first
For space complexity, it has O(1): the no new variable is created to store the number array while sorting. Sorting is done in the original array

Selection sort is a simple sorting algorithm and is useful in cases where there is a need to preserve memory



###Implementation
```js
// Selection Sort
/**
 * @desc    through each index in the array comparing it with 
 *          other number in the array while arranging smallest 
 *          number first
 *          expects "nums" which is the array to be sorted.
 * @params  nums: number[]
 * @return nums: number[]
*/
const sortBySelection = (nums) => {
  let count = 0
  let pointer = count + 1

  while (count < nums.length - 1) {

    const nextMinIndex = findNextMinIndex(nums, pointer)
    if (nums[count] > nums[nextMinIndex]) {
      [nums[count], nums[nextMinIndex]] = [nums[nextMinIndex], nums[count]]
    }
    count++
    pointer++
  }

  return nums
}

/**
 * @desc    iterates the next items in the array to find 
 *          the index of the next smallest number.
 *          expects "nums" and "pointer"
 *          nums: the original array to be sorted
 *          pointer: pointer to the start of the rest number
 *              in the array
 * @params  nums: number[]
 * @params  pointer: number
 * @return minValueIndex: number
*/
function findNextMinIndex(nums, pointer) {
  let minValueIndex = pointer

  while (pointer < nums.length) {

    if (nums[pointer] < nums[minValueIndex]) {
      minValueIndex = pointer
    }

    pointer++
  }

  return minValueIndex;
}

console.log(sortBySelection([6,5,5,3,2,2])) // [ 2, 2, 3, 5, 5, 6 ]
```
