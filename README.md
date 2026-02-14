# Bubble Sort
## 🔎 Overview

**Bubble Sort** is one of the simplest sorting algorithms. It repeatedly steps through the list, compares elements, and swap them if they are in the wrong order

This process continues until the list is fully sorted.

It is known for being:
-   ✅ Easy to understand and implement
-   ✅ Stable (keeps equal elemennts in original order)
-   ✅ In-place (no extra memory needed)
-   ❌ Very slow for large datasets

## ⚙️ How Bubble Sort Works

### Step 1 — Compare Adjacent Elements
Start from the first element and compare it with the next one.

Example:

```[5, 3, 8, 4]```

Compare ```5``` and ```3``` → swap:

```[3, 5, 8, 4]```

### Step 2 — Continue Swapping

Compare next pair:

5 and 8 → no swap  
8 and 4 → swap

Array becomes:

```[3, 5, 4, 8]```

Largest value **“bubbles up”** to the end.


### Step 3 — Repeat Passes

Repeat the process for the remaining unsorted portion until no swaps occur.

Final result:

```[3, 4, 5, 8]```

### ⏱️ Time & Space Complexity
| ⏱️ Case       | Time Complexity |
|---------------|----------------|
| Best Case     | O(n) (optimized vesion)    |
| Average Case  | O(n)     |
| Worst Case    | O(n)     |

**Space Complexity:** O(1)




## 📁 Python Implementation


```python
# %% [markdown]
# # Bubble Sort

# %%
"""
BUBBLE SORT: A COMPREHENSIVE GUIDE & VISUALIZATION
This project demonstrates the mechanics of the Bubble Sort algorithm, 
explaining the logic step-by-step and providing a visual representation 
of how elements 'bubble' to the top.
"""

import time

# %%
def bubble_sort_visualized(arr):
    """
    Sorts a list of numbers using the Bubble Sort algorithm and
    prints a visualization of each step
    """

    # Get the length of the array
    n = len(arr)

    # We loop through the entire list n times
    # Each pass places the next largest element in its correct position
    for i in range(n):
        # Flag to track if any swaps happened in this pass
        # This is an optimization: if no swaps occur, th list is already sorted
        swapped = False

        print(f"\n----- Pass {i + 1} -----")

        # Last i elements are already in place, so we ignore them (n - i - 1)
        for j in range(0, n - i - 1):
            
            # VISUALIZATION: Show the current state and two numbers being compared
            visualize_step(arr, j, j + 1)

            # Compare the current element with the next one
            # If the current is larger, they are out of order
            if arr[j] > arr[j +1]:
                # Swap the elements
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

                # Set swapped to True because we performed an action
                swapped = True
                print(f" [SWAP] {arr[j + 1]} is larger than {arr[j]}, moving it right.")
            else:
                print(f" [KEEP] {arr[j]} is smaller than {arr[j + 1]}, no swap needed")

        
        # If no two elements were swapped by inner loop, then break
        if not swapped:
            print("\nOPTIMIZATION: No swaps occurred this pass. The list is sorted!")


    return arr


# %%
def visualize_step(arr,idx1,idx2):
    # Creates an ASCII bar chart representation of the array
    # Highlist the indices being compared

    max_val = max(arr) if arr else 1
    print("\n Current State:")
    for i, val in enumerate(arr):
        # Create a bar of "#" characters proportional to the value
        bar = "#" * val
        padding = " " * (max_val - val)

        # Highlight the elements currently being compared with arrows
        pointer = "<-- COMPARING" if i == idx1 or i == idx2 else ""

        print(f" {val:2} | {bar}{padding} {pointer}")

# %%
def run_examples():
    # Runs the bubble sort on various types of data

    # Example 1: Standard Unsorted List
    print("=" * 50)
    print("EXAMPLE 1: RANDOMIZED UNSORTED LIST")
    print("=" * 50)
    sample_1 = [5,2,9,1,5,6]
    print(f"Original: {sample_1}")
    result_1 = bubble_sort_visualized(sample_1)
    print(f"\nFinal Sorted Result: {result_1}")

    # Example 2: Already Sorted List (Demonstrating Optimization)
    print("="*50)
    print("EXAMPLE 2: ALREADY SORTED LIST")
    print("="*50)
    sample_2 = [10,20,30,40]
    print(f"Original: {sample_2}")
    result_2 = bubble_sort_visualized(sample_2)
    print(f"\nFinal Sorted Result: {result_2}")

    # Example 3: Reversed List (Worst Case Scenario)
    print("="*50)
    print("EXAMPLE 3: REVERSED LIST (WORST CASE)")
    print("="*50)
    sample_3 = [8,6,4,2]
    print(f"Original: {sample_3}")
    result_3 = bubble_sort_visualized(sample_3)
    print(f"\nFinal Sorted Result: {result_3}")

# %%
if __name__ == "__main__":
    # Start the educational tour
    print("WELCOME TO THE BUBBLE SORT TUTORIAL")
    print("Concept: Larger elements 'bubble' to the end of the list like air bubbles in water.")
    print("Time Complexity: O(n^2) in worst case.")
    print("Space Complexity: O(1) - it sorts 'in-place'.")
    
    run_examples()



```

















👍 Advantages

-   Very easy to understand

-   Good for teaching sorting concepts

-   Works well for very small datasets

-   Detects already sorted lists quickly (optimized version)

## 👎 Disadvantages

-   Extremely slow for large lists

-   Inefficient compared to merge sort, quick sort, or heap sort

-   Performs many unnecessary comparisons



## 📌 When to Use Bubble Sort

Use Bubble Sort when:

-   Teaching algorithm basics

-   Sorting very small datasets

-   Checking if a list is already nearly sorted

-   Simplicity matters more than speed

## 🏁 Summary

Bubble Sort is a beginner-friendly sorting algorithm that demonstrates how comparisons and swaps work.
While inefficient for large datasets, it remains useful for education and small-scale applications.