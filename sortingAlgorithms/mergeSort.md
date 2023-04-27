# Merge Sort

Merge sort is a stable, comparison based, recursive, divide and conquer algorithm which repeatedly braeaks down a list of elements into smaller and smaller parts, then slowly puts it together sorted

Time Complexity: O(n log n)

Space Complexity: O(n)

### Implementation

```js

// Merge Sort

/**
 * 
 * @desc    Merge Sort Algortihm
 * @params nums: number[]
 * @return nums: number[]
 * 
*/

const mergeSort = (nums) => {
  // Base case
  if (nums.length <= 1) return nums

  let mid = Math.floor(nums.length/ 2)

  // Recrusively break the number into smaller problem
  let left = mergeSort(nums.slice(0, mid))
  let right = mergeSort(nums.slice(mid))
  
  return merge(left, right)
}


// Merge function to build a sorted aray
const merge = (left, right) => {
  let sortedArr = []

  while (left.length && right.length) {

    // Compare left and right elements
    // remover the smallest element compared
    // Put the smallest element in sortedArr
    //compare left and right until either left is empty or right is empty

    left[0] < right[0] ?
    sortedArr.push(left.shift()) : sortedArr.push(right.shift())
  }

    // return sortedArr and any element in left or right after comparison has completed
  return [...sortedArr, ...left, ...right]
}

console.log(mergeSort([2,7,4,1,8])) // [ 1, 2, 4, 7, 8 ]


```