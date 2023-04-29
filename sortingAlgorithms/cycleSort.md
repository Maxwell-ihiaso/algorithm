# Cycle Sort

Cycle sort is an unstable, in-place, comparison-based sorting algorithm which sorts the list using a set of cycles. Each cycle consists of placing an element at it's sorted index in the data-set, taking the element at the sorted index and placing it at it's sorted index, and repeating until the list is sorted

Time Complexity: O(n^2); when n is in range of [1, n] or [0, n], time complexity is O(n) as implemented below
Space Complexity: O(1)

### Implementation 

To understand the implementation of Cycle sort, we must understand what it means for an element to be in it's sorted index. An element is said to be in it's sorted index if it is at an index that is equal to the number of elements it is greater than in the array.

This definition is very instrumental in the implementation of cycle sort

```js

const cycleSort = (nums) => {
  
  let arrCopy = nums.slice(); // create a reference of the original array
  let numMap = {} // to keep track of duplicates
  let cycleStart = 0; // used for transversing the array
  let current = null // current element in cycle
  let currentPosition = null // sorted index for the current element

  while (cycleStart < nums.length) {
    current = nums[cycleStart];
    // get the sorted index of the current element
    currentPosition = arrCopy.filter(num => num <= current).length - 1;

// run a cycle to position the current element in
// its sorted index then also position the exisiting
// element in the sorted index, where it should be
    while(!(current in numMap) || arrCopy.filter(num => num === current).length !== numMap[current]) {
      // To figure when an element is duplicate, we
      // maintain a map that keep counts of how many
      // times we encounter the same element in a 
      // different position.
      if (!(current in numMap)) numMap[current] = 1;
      else numMap[current] += 1
      
      // Place current element in its sorted index and make the
      // element replaced the current element
      current = nums.splice(currentPosition, 1, current)[0]

      // Get the sorted index of the replaced element
      currentPosition = arrCopy.filter(num => num <= current).length - 1;

      // if current element is a duplicate, update its sorted index
      currentPosition = current in numMap ? ( currentPosition - numMap[current]) : currentPosition
    }
    cycleStart++
  }
  return nums
}


console.log(cycleSort([3,4,5,1,2, 1, 1, 1, 1])); // Outputs: [ 1, 1, 1, 1, 1, 2, 3, 4, 5 ]
console.log(cycleSort([4,5,6,7,0,1,2])); // Outputs: [ 0, 1, 2, 4, 5, 6, 7 ]
console.log(cycleSort([11,13,1, 2, 15,17])); //Outputs:  [ 1, 2, 11, 13, 15, 17 ]
console.log(cycleSort([])); // Outputs: []

// Time Complexity: O(n^2)
// Space Complexity: O(1)

```

if n is in range [0, n], the algorithm would be implemented in this way

```js

const cycleSort = (nums) => {
  let pos = 0;

  while (pos < nums.length) {
    // as array is of 0 based indexing so the
    // correct position or index number of each
    // element is element i.e. 0 will be at 0th
    // index similarly 1 correct index will be 1 so
    // on...
    let correctPosition = nums[pos]

    if (nums[pos] !== nums[correctPosition]) {
        [ nums[pos], nums[correctPosition] ] = [ nums[correctPosition], nums[pos]];
    } else {
        // if element is at its correct position
        // just increment i and check for remaining
        // array elements
        pos++;
    }
  }

    return nums
}

// Time Complexity: O(n)
// Space Complexity: O(1)

```

if n is in range [1, n], the algorithm would be implemented in this way

```js

const cycleSort = (nums) => {
  let pos = 0;

  while (pos < nums.length) {
    // as array is of 1 based indexing so the
    // correct position or index number of each
    // element is element - 1 i.e. 1 will be at 0th
    // index similarly 2 correct index will be 1 so
    // on...
    let correctPosition = nums[pos] - 1

    if (nums[pos] !== nums[correctPosition]) {
        [ nums[pos], nums[correctPosition] ] = [ nums[correctPosition], nums[pos]];
    } else {
        // if element is at its correct position
        // just increment i and check for remaining
        // array elements
        pos++;
    }
  }

    return nums
}

// Time Complexity: O(n)
// Space Complexity: O(1)

```