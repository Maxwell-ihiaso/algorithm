# Quick Sort
Quick sort is an efficieint, in-place, divide-and-conquer algorithm which sort elements by partitioning the data sets into two parts. Then recursively sorting each parts independently.

> to partition the  data sets we use a pivot

Time Complexity:

best case - O(n.logn), worst case (O(n^2))

Space Complexity:

best case (O(logn)), worst case (O{n})


> Best case fro tiem complexity happens when partitioning is done in the center, worst case time complexity happens when partitioning is done in the begining or end

### Implementation
```js

/**
 * @desc    Quick sort in-place, divide-and-conquer sort
 *          implementation.
 * @params  nums: number[]
 *          low: number; determined by the computer
 *          high: number; determined by the computer
 * @retuns  nums: number[]; sorted array
*/
const quickSort = (nums, low, high) => {
  if (nums.length <= 1) {
    return nums
  }

  low = low || 0;
  high = high || nums.length - 1;

  // get pivot via partitioning
  let pivot = partitioning(nums, low, high);

  // run recursion
  if (low < pivot - 1) {quickSort(nums, low, pivot - 1)}
  if (pivot + 1 < high) {quickSort(nums, pivot + 1, high)}
  
return nums
}


// Partitioning method
/**
 * @desc    Method to find pivot and place it in its
 *          sorted position.
 * @params  nums: number[]
 *          l: number
 *          h: number
 * @retuns  h: number; position of the pivot element
*/
const  partitioning = (nums, l, h) => {
    // select an element to be considered as pivot
  let refIndex = Math.floor(Math.random() * h)

  while (l < h) {
    while (nums[l] <= nums[refIndex]) {l++;}
    while (nums[h] > nums[refIndex]) {h--;}
    // swap items higher than pivot to right and
    // items lower than pivot to the left
    if (nums[l] > nums[h] && l < h) [ nums[l], nums[h] ] = [ nums[h], nums[l]]
  }

// place pivot element in its sorted element
  [nums[refIndex], nums[h]] = [nums[h], nums[refIndex]];
  return h; // index of pivot element
}



console.log(quickSort([5, 6, 3, 7, 1, 8, 9])) // [ 1, 3, 5, 6, 7, 8, 9 ]
console.log(quickSort([4,1,6,8,9,5,3])) // [ 1, 4, 3, 5, 6, 8, 9 ]


```