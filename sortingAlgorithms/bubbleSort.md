# Bubble Sort
Bubble sort is a simple, in-place, stable sorting algorithm which repeatedly swaps elements that are out of order until the list is sorted.

> By stable, it means that Bubble sort retain the order of duplicate element in the array to be sorted

>By in-place, it means no new array is created, the sorting is done on the unsorted array.

Time complexity: O(n^2)

Space complexity: O(1)

### Implementation
```js

// Bubble Sort

/**
 * @desc    sort an array using the bubble sort
 *          We maintain a swappedValues variable and a
 *          pointer to the current element being compared.
 *          Maintaining a swappedValues ensures that we only have one
 *          pass if the array is already sorted.
 *          for sortedArray, time complexity is O(n)
 * @params  nums: number[]
 * @return  nums: number[]
*/
const bubbleSort = (nums) => {
  let swappedValues = true
  let current = 0

  while (swappedValues) {
    swappedValues = false
    while (current < nums.length - 1) {
      if (nums[current] > nums[current + 1]) {
        [ nums[current], nums[current + 1] ] = [ nums[current + 1], nums[current] ]
        swappedValues = true
      }
      current++
    }
    current = 0
  }
  return nums
}

// Usage
console.log(bubbleSort([3,6,5,1,5,3,2,2])) // [ 1, 2, 2, 3, 3, 5, 5, 6 ]

```