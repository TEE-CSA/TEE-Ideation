---
title: Mini-Project Ideation and Planning
description: Blog about plans
type: plan
courses: {'csa': {'week': 13}}
---

# Our Idea 

We want to create a race game between multiple sorting algorithms and Fibonacci methods that will allow users to see which sorting algorithm is the most efficient. To incorporate fibonacci, we will make two different game modes: one for sorting and one for fibonacci.

## Canva Outline

> Fibonacci Race

<img src="https://github.com/realethantran/fastpages_EthanT/assets/109186517/746d9527-9718-453c-8bbf-e73ac5bac750" width="100%">

> Sorting Race

<img src="https://github.com/realethantran/fastpages_EthanT/assets/109186517/e2750a41-4e29-4f1c-b576-3a7d5db824b8" width="100%">

## Sorting

- Treating each sorting algorithm as their separate "avatars" or characters for the player
- Comparing the time that it takes for each algorithm to sort out a list of numbers of size n from least to greatest
- Users choose the avatar - the algorithm - that they think will be fastest
- They also input the amount of integers in the array and our code will randomly generate that amount

## Fibonacci

- Will be similar to sorting race
- Instead of sorting algorithms, different fibonacci methods represent the avatars
    - Different methods may be for loop, while loop, recursion, matrices, etc.
- Users can choose some Fibonacci number and see how long each method takes to generate that number

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

# Betting 

- The user will start the game with a fixed number of points (ex. 500) 
- The user will be able to bet a certain number of points on an algorithm winning the race (ex. could be 150 points)
- Two possible outcomes
    - If their guess is correct, the user can win double the amount that they bet (continuing from the above example, the user would win 150 x 2 = 300 points, giving them a total of 800 points)
    - If their guess is wrong, the user will lose how ever much they bet (ex. they would lose 150 points, bringing their points down to 350)

```java
// pseudo code

public class Points {
    int score = 500;
    int bet;

    boolean isCorrect;

    if(isCorrect){
        score += 2*bet;
    } else {
        score -= bet;
    }

}
```
