# Odd Even Sort

Odd even sort is a variation of the Bubble sort algorithm and aims at improving the efficiency of the Bubble sort algorithm. It is a stable and comparison based algortithm that does sorting on an even and odd index until all elements to be sorted are well sorted.

Time Complexity: O(n^2)

Space Complexity: o(1)

### Implementation 
```js

// ODD EVEN ALGORITHM

/**
 * @desc    Odd-Even Algorithm
 *          used to sort an array as a variation of the
 *          Bubble sort
 * @params  nums: number[]
 * @return  nums: number[]
 * 
*/
const oddEvenSort = (nums) => {
    let isSorted = false;
    let oddCount = 1;
    let evenCount = 0;

    while (!isSorted) {
        isSorted = true;

        // Sorting based on ODD index
        while (oddCount < nums.length - 1) {
            if (nums[oddCount] > nums[oddCount + 1]) {
                isSorted = false;
                [ nums[oddCount], nums[oddCount + 1] ] = [ nums[oddCount + 1], nums[oddCount] ]
            }
            oddCount += 2;
        }

        // Sorting based on EVEN index
        while (evenCount < nums.length - 1) {
            if (nums[evenCount] > nums[evenCount + 1]) {
                isSorted = false;
                [ nums[evenCount], nums[evenCount + 1] ] = [ nums[evenCount + 1], nums[evenCount] ]
            }
            evenCount += 2;
        }

        oddCount = 1;
        evenCount = 0;
    }

    return nums
}

console.log(oddEvenSort([5,2,7,1,8,3,9,5,4])) // [ 1, 2, 3, 4, 5, 5, 7, 8, 9 ]

```