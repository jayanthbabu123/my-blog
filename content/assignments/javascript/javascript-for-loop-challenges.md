+++
title = 'Javascript for Loop Challenges with Functions - 2'
date = 2024-04-16T17:10:23+05:30
draft = false
+++

# JavaScript Exercises: Intermediate `for` Loop Challenges

Sharpen your JavaScript skills with these intermediate exercises that focus on using traditional `for` loops within functions to manipulate strings, numbers, objects, and arrays. Each exercise requires you to write a function that returns the output.

## Exercises

## 1. Sum of an Array

**Question:** Write a function `sumArray` that takes an array of numbers and returns the sum of all elements.

**Required Output for `[1, 2, 3, 4]`:** `10`

**Required Output for `[]`:** `0`

**Required Output for `[1]`:** `1`

## 2. Reverse String

**Question:** Write a function `reverseString` that takes a string and returns it reversed.

**Required Output for "hello":** `"olleh"`

**Required Output for "world":** `"dlrow"`

**Required Output for "":** `""`

## 3. Find Min and Max

**Question:** Write a function `findMinMax` that returns the minimum and maximum of an array of numbers as an object `{ min, max }`.

**Required Output for `[2, 3, 1, 4]`:** `{ min: 1, max: 4 }`

**Required Output for `[]`:** `{ min: undefined, max: undefined }`

**Required Output for `[1]`:** `{ min: 1, max: 1 }`

## 4. Count Characters

**Question:** Write a function `countChars` that takes a string and returns an object with the counts of each character.

**Required Output for "hello":** `{ h: 1, e: 1, l: 2, o: 1 }`

**Required Output for "world":** `{ w: 1, o: 1, r: 1, l: 1, d: 1 }`

**Required Output for "":** `{}`

**Required Output for "a":** `{ a: 1 }`

## 5. Multiplication Table

**Question:** Write a function `multiplicationTable` that takes a number and returns its multiplication table up to 10 as an array.

**Required Output for `3`:** `[3, 6, 9, 12, 15, 18, 21, 24, 27, 30]`

**Required Output for `5`:** `[5, 10, 15, 20, 25, 30, 35, 40, 45, 50]`

**Required Output for `7`:** `[7, 14, 21, 28, 35, 42, 49, 56, 63, 70]`

## 6. Filter Odd Numbers

**Question:** Write a function `filterOdds` that filters out odd numbers from an array and returns the remaining numbers.

**Required Output for `[1, 2, 3, 4, 5]`:** `[1, 3, 5]`

**Required Output for `[1, 2, 3, 4, 5]`:** `[2, 4]`

**Required Output for `[]`:** `[]`

## 7. Convert to Camel Case

**Question:** Write a function `toCamelCase` that converts a string of words separated by spaces or underscores to camelCase.

**Required Output for "hello world":** `"helloWorld"`

**Required Output for "hello_world":** `"helloWorld"`

## 8. Rotate Array

**Question:** Write a function `rotateArray` that rotates an array to the right by a given number of steps.

**Required Output for `([1, 2, 3, 4, 5], 2)`:** `[4, 5, 1, 2, 3]`

**Required Output for `([1, 2, 3, 4, 5], 3)`:** `[3, 4, 5, 1, 2]`

## 9. Flatten Array

**Question:** Write a function `flattenArray` that flattens an array of arbitrarily nested arrays of integers into a flat array.

**Required Output for `[1, [2, [3, 4], 5]]`:** `[1, 2, 3, 4, 5]`

**Required Output for `[1, 2, [3, [4, [5, [6, 7]]]]]`:** `[1, 2, 3, 4, 5, 6, 7]`

## 10. Find Duplicate Numbers

**Question:** Write a function `findDuplicates` that finds and returns duplicate numbers from an array.

**Required Output for `[1, 2, 3, 2, 4, 3]`:** `[2, 3]`

**Required Output for `[1, 2, 3, 4, 5]`:** `[]`

## 11. Capitalize Words

**Question:** Write a function `capitalizeWords` that takes a string and capitalizes the first letter of each word.

**Required Output for "capitalize every word":** `"Capitalize Every Word"`

**Required Output for "hello world":** `"Hello World"`

## 12. Unique Characters

**Question:** Write a function `uniqueChars` that checks if a string contains only unique characters and returns `true` or `false`.

**Required Output for "abcdef":** `true`

**Required Output for "hello":** `false`

## 13. Array Intersection

**Question:** Write a function `arrayIntersection` that returns the intersection of two arrays.

**Required Output for `([1, 2, 3], [2, 3, 4])`:** `[2, 3]`

**Required Output for `([1, 2, 3], [4, 5, 6])`:** `[]`

## 14. Sum of Digits

**Question:** Write a function `sumDigits` that takes a number and returns the sum of its digits.

**Required Output for `1234`:** `10`

**Required Output for `9876`:** `30`

## 15. Is Anagram

**Question:** Write a function `isAnagram` that checks if two provided strings are anagrams of each other.

**Required Output for ("listen", "silent"):** `true`

**Required Output for ("hello", "world"):** `false`

## 16. Remove Specific Element

**Question:** Write a function `removeElement` that takes an array and an element to remove, returning the array without that element.

**Required Output for `([1, 2, 3, 4, 5], 3)`:** `[1, 2, 4, 5]`

**Required Output for `([1, 2, 3, 4, 5], 6)`:** `[1, 2, 3, 4, 5]`

## 17. Count Words

**Question:** Write a function `countWords` that takes a string and returns the number of words in the string.

**Required Output for "This is a test string":** `5`

**Required Output for "":** `0`

## 18. Sort Numbers

**Question:** Write a function `sortNumbers` that takes an array of numbers and returns a sorted array in ascending order using a sorting algorithm implemented with a `for` loop.

**Required Output for `[34, 7, 23, 32, 5]`:** `[5, 7, 23, 32, 34]`

**Required Output for `[]`:** `[]`

## 19. Are Arrays Equal

**Question:** Write a function `areArraysEqual` that checks if two arrays contain the same elements in the same order.

**Required Output for `([1, 2, 3], [1, 2, 3])`:** `true`

**Required Output for `([1, 2, 3], [3, 2, 1])`:** `false`

## 20. Find Longest Consecutive Sequence

**Question:** Write a function `longestConsecutive` that finds the longest sequence of consecutive integers in an unsorted array.

**Required Output for `[100, 4, 200, 1, 3, 2]`:** `4` (The sequence is `[1, 2, 3, 4]`)


## Conclusion

By practicing these exercises you will be able to use `for` loops and `for...of` loops to manipulate strings, numbers, objects, and arrays. You will also be able to use string methods to manipulate and manipulate strings.


