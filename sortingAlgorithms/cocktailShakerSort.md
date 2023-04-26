# Cocktail Shaker Sort
Cocktail Shaker Sort is a simple, in-place, stable sorting algorithm which repeatedly swaps elements that are out of order until the list is sorted.

> By stable, it means that Bubble sort retain the order of duplicate element in the array to be sorted

>By in-place, it means no new array is created, the sorting is done on the unsorted array.

This is a variation of the bubble sort algorithm. While it shares similar time complexity with bubble sort, it is relatively faster than bubble sort

Time complexity: O(n^2)

Space complexity: O(1)

### Implementation
```js

// Cocktail Shaker Sort

/**
 * @desc    sort an array using the cocktail shaker sort
 *          We maintain a swappedValues variable and a
 *          pointer to the current element being compared.
 *          Maintaining a swappedValues ensures that we only have one
 *          pass if the array is already sorted.
 *          
 *          We compare the elements in the array in a forward and
 *          backward movement in one pass (loop)
 * 
 *          For sortedArray, time complexity is O(n)
 * @params  nums: number[]
 * @return  nums: number[]
*/

const cocktailShakerSort = (nums) => {
  let swappedValues = true
  let current = 0

  while (swappedValues) {
    swappedValues = false

    // forward comparison to move the largest
    // number to the end
    while (current < nums.length - 1) {
      if (nums[current] > nums[current + 1]) {
        [nums[current], nums[current + 1]] = [ nums[current + 1], nums[current]]
        swappedValues = true
      }
      current++
    }

    // Backward comparison to move the smallest
    // number to the begining
    while (current > 0) {
      if (nums[current] < nums[current - 1]) {
        [nums[current], nums[current - 1]] = [ nums[current - 1], nums[current]]
        swappedValues = true
      }
      current--
    }
    
  }
  return nums
}

console.log(cocktailShakerSort([3,6,5,0,1,5,3,2,2])) // [ 0, 1, 2, 2, 3, 3, 5, 5, 6 ]

```