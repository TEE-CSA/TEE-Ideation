---
title: Mini-Project Ideation and Planning
description: Blog about plans
type: plan
courses: {'csa': {'week 13': None}}
---

# Our Idea 

We want to create a race game between multiple sorting algorithms that will allow users to see which sorting algorithm is the most efficient. To incorporate fibonacci, we will make two different game modes: one for sorting and one for fibonacci.

## Sorting

- Treating each sorting algorithm as their separate "avatars" or characters for the player
- Comparing the time that it takes for each algorithm to sort out a list of numbers of size n from least to greatest
- Also a game mode for the player can choose from (along with fibonacci)

### Inheritance

- Create a superclass for the common attributes of each sorting algorithm (ex. class Sort)
- Create multiple subclasses for the specific sorting algorithms
    - Set up before writing the actual methods for bubble sort, merge sort, etc.


```python

public class SortingController {

    @PostMapping("/sort")
    public int[] sortNumbers(@RequestBody int[] numbers, @RequestParam String algorithm) {
        switch (algorithm.toLowerCase()) {
            case "merge":
                return mergeSort(numbers);
            case "selection":
                return selectionSort(numbers);
            case "bubble":
                return bubbleSort(numbers);
            case "insertion":
                return insertionSort(numbers);
            default:
                throw new IllegalArgumentException("Invalid sorting algorithm: " + algorithm);
        }
    }

    // Merge Sort
    private int[] mergeSort(int[] array) {
        // ...
        return array;
    }

    // Selection Sort
    private int[] selectionSort(int[] array) {
        // ...
        return array;
    }

    // Bubble Sort
    private int[] bubbleSort(int[] array) {
        // ...
        return array;
    }

    // Insertion Sort
    private int[] insertionSort(int[] array) {
        // ...
        return array;
    }
}
   
```
