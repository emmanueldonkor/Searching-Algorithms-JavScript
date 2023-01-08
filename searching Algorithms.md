### Introduction

### Searching Algorithms

<p> 
Search algorithms are methods used to find specific information within a data structure or to solve a problem within a defined search space. The efficiency of these algorithms can be measured by their computational complexity, which refers to the maximum amount of time it takes for the algorithm to run. For example, a binary search algorithm has a complexity of O(log n), meaning that the maximum number of operations needed to find the desired information increases logarithmically as the size of the search space increases.
</p>


<h1>Most Popular Searching Algorithms </h1>

<ul>
  <li><strong>Linear Search:</strong> This is the simplest search algorithm, where the search starts from the first element of the list and compares each element with the target element until a match is found or the end of the list is reached.
Example:


function linearSearch(arr, target) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === target) {
      return i;
    }
  }
  return -1;
}
</li>
  <li><strong>Binary Search:</strong> This is an efficient search algorithm that works on sorted lists. It starts by comparing the target element with the middle element of the list. If the target element is smaller than the middle element, then it searches the left half of the list. If the target element is larger than the middle element, then it searches the right half of the list. This process is repeated until the target element is found or it is determined that the element is not present in the list.
Example:

//Searching for a and elment in an array 
function binarySearch(arr, target) {
  let start = 0;
  let end = arr.length - 1;
  while (start <= end) {
    let mid = Math.floor((start + end) / 2);
    if (arr[mid] === target) {
      return mid;
    } else if (arr[mid] < target) {
      start = mid + 1;
    } else {
      end = mid - 1;
    }
  }
  return -1;
}
</li>
  <li><strong>Jump Search:</strong> This is an efficient search algorithm for sorted lists that involves jumping over a fixed number of elements (called "steps") to find the target element. It is similar to binary search, but it does not always divide the list into two equal parts.
Example:


function jumpSearch(arr, target) {
  const n = arr.length;
  const step = Math.floor(Math.sqrt(n));
  let prev = 0;
  while (arr[Math.min(step, n) - 1] < target) {
    prev = step;
    step += Math.floor(Math.sqrt(n));
    if (prev >= n) {
      return -1;
    }
  }
  while (arr[prev] < target) {
    prev++;
    if (prev === Math.min(step, n)) {
      return -1;
    }
  }
  if (arr[prev] === target) {
    return prev;
  }
  return -1;
}
</li>
  
<li><strong>Exponentiation Search:</strong> This is a search algorithm that works on sorted lists and involves repeated squaring to find the position of the target element. It starts by finding the nearest power of 2 that is less than or equal to the target element, and then uses binary search to find the target element in the subarray between the nearest power of 2 and the next power of 2.
Example:


function exponentiationSearch(arr, target) {
  if (arr[0] === target) {
    return 0;
  }
  let i = 1;
  while (i < arr.length && arr[i] <= target) {
    i *= 2;
  }
  return binarySearch(arr, target, i / 2, Math.min(i, arr.length));
}

function binarySearch(arr, target, low, high) {
  if (high >= low) {
    const mid = low + Math.floor((high - low) / 2);
    if (arr[mid] === target) {
      return mid;
    } else if (arr[mid] < target) {
      return binarySearch(arr, target, mid + 1, high);
    } else {
      return binarySearch(arr, target, low, mid - 1);
    }
  }
  return -1;
}
</li>
  <li><strong>Fibonacci Search:</strong> This is a search algorithm that works on sorted lists and involves using Fibonacci numbers to find the position of the target element. It starts by finding the nearest Fibonacci number that is less than or equal to the length of the list, and then uses binary search to find the target element in the subarray between the nearest Fibonacci number and the next Fibonacci number.
Example:


function fibonacciSearch(arr, target) {
  const n = arr.length;
  let fibM2 = 0;
  let fibM1 = 1;
  let fibM = fibM2 + fibM1;
  while (fibM < n) {
    fibM2 = fibM1;
    fibM1 = fibM;
    fibM = fibM2 + fibM1;
  }
  let offset = -1;
  while (fibM > 1) {
    const i = Math.min(offset + fibM2, n - 1);
    if (arr[i] < target) {
      fibM = fibM1;
      fibM1 = fibM2;
      fibM2 = fibM - fibM1;
      offset = i;
    } else if (arr[i] > target) {
      fibM = fibM2;
      fibM1 = fibM1 - fibM2;
      fibM2 = fibM - fibM1;
    } else {
      return i;
    }
  }
  if (fibM1 && arr[offset + 1] === target) {
    return offset + 1;
  }
  return -1;
}
</li>
</ul>
<!--All theese algorithms will be explained in each folder -->

<p>In JavaScript there are a lot of built in functions that uses the searching algorithms</p>

<ul>
  <li>indexOf(): This method searches for a specified item in an array and returns its index if found, or -1 if not found.</li>
  <li>lastIndexOf(): This method searches for a specified item in an array, starting from the end of the array and returns its index if found, or -1 if not found.</li>
  <li>includes(): This method searches for a specified item in an array and returns a boolean value indicating whether the item was found or not.</li>
  <li>find(): This method searches for the first element in an array that satisfies a provided testing function and returns the value of that element.</li>
  <li>findIndex(): This method searches for the index of the first element in an array that satisfies a provided testing function and returns the index of that element.</li>
  <li>search(): This method searches for a specified value in a string and returns the position of the match, or -1 if not found.</li>
 
</ul>


<!--  All algorithms will be explained in it's on folder-->
<h1>Thanks for reading </h1>