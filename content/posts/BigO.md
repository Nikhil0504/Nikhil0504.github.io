---
title: "Big O Notation"
description: "Explanation of the Big O Notation"
date: 2021-11-10T11:40:11+05:30
draft: false
---

{{< katex >}} 

{{< lead >}}
This post is based on one of my school presentations I did this year.
{{< /lead >}}

# Introduction

Alogrithms is essential for performing calculations, data processing or any other tasks for that matter. As an 
effective method, an algorithm can be expressed within a finite amount of space and time, and in a well-defined 
formal language for calulating a function.

Big O Notation is a way measure an algorithm's efficiency. It is used to depict an algorithm's growth rate that determines 
its performance when the input size grows.


{{< alert >}} **Note**: I could bore you with all mathematics and formal definitions but since I am too lazy to write and there are
better people than me who can explain those better you can just 
see this [link](https://en.wikipedia.org/wiki/Big_O_notation#Formal_definition) {{< /alert >}}

---

# Comparison
Big O Notation is representated as \\(O()\\) which essentially means it will take some value for some particular amount of steps.

Let's say for instance we have two algorithms with complexities \\(O(n^2)\\) and \\(O(2^n)\\)
We will get the following table:
|   Size N   | 10   | 20      | 40          | 100                |
|:----------:|------|---------|-------------|--------------------|
| \\(N^2\\) | 100  | 400     | 1600        | 10000              |
| \\(2^N\\) | 1024 | 1048576 | \\(10^{12}\\) | \\(1.26 × 10^{30}\\) |

Performance of algorithm is *inversely proportional* to the wall clock time it records for a given input size.

We usually consider the term that will affect the algorithm the **most**. For example if we have an algorithm depending on 
the value of \\(n\\) with a performance of \\(ax^2 + bx + c \\) we would just the sqaured term as that would be affected
the most. So we can simply say that this algorithm has a performance of \\(O(N^2)\\)

---
# Examples

## Linear Search
Let's say we want to search for a number from 1 to 10

Our first strategy is to start with the first number of the array and move up by one until we find our target number. 
Our algorithm steps would look something like this.
1. Start at the beginning
2. Compare the value with the target
3. Move to the next value
4. Reach end of the list

In round 1, we choose number one; that’s not correct, so we move to round 2 and eliminate number one as an option. 
Step 2 is also not correct, and we continue all the way until we select number ten.

In the worst-case senario, this is not very efficient. We would have to thorugh the entire list one-by-one to get
our answer. The Big O notation for Linear Search is \\(O(N)\\). The complexity is directly related to the size of 
the inputs — the algorithm takes an additional step for each additional data element.

{{< highlight python >}}

def linear_search(array, x):
    for i in range(len(array)):
        if array[i] == x:
            return i
    return "Not found in array"
{{< /highlight >}}

**Time Complexity:**  <kbd>\\(O(N)\\)</kbd>

**Space Complexity:**  <kbd>\\(O(1)\\)</kbd>

## Binary Search
Let's try out a different strategy. The most critcal part over here would be to keep the list in order.

Now instead of starting from first, we start from the middle of the list. We check to see whether we have chosen 
the target number. If not, we check whether the number is smaller or larger than our choice. In either case, 
we eliminate half of the list that doesn’t include our target. Then we select a number in the middle of the remaining values.

Our algorithm steps would look something like this.
1. Find the midpoint of the list
2. Compare the midpoint with the target
3. If our value and the target match we stop — we’ve found our target
4. If our value is smaller than the target, we make a new list ranging from the midpoint plus one to the largest value.
5. If our value is larger than the target, we make a new list ranging from the smallest value to the midpoint minus one.
6. Repeat until we find the target or reach that last element, and it does not match the target.

This is efficient because it eliminates half of the list in each pass. Amazingly, if we were to pick a number between 
one and a million, the worst case would be 20 guesses.

In general, the worst-case scenario of a Binary Search is \\(log(n + 1)\\). The Big O notation for Binary Search is 
\\(O(log N)\\). In contrast to \\(O(N)\\) which takes an additional step for each data element, \\(O(log N)\\) means that the 
algorithm takes an additional step each time the data doubles.

{{< highlight python >}}

def binary_search(array, x):
    left = 0
    right = len(arr) - 1

    while left <= right:
        mid_point = (left + right) // 2

        if target < arr[mid_point]:
            right = mid_point - 1
        elif target > arr[mid_point]:
            left = mid_point + 1
        else:
            return mid_point
    return "Not found in array"
{{< /highlight >}}

**Time Complexities:**  

- *Best case complexity:* <kbd>\\(O(1)\\)</kbd>
- *Average case complexity:* <kbd>\\(O(log(N))\\)</kbd>
- *Worst case complexity:* <kbd>\\(O(log(N))\\)</kbd>

**Space Complexity:**  <kbd>\\(O(1)\\)</kbd>

---

# Further Reading
If you want to learn more about Big O notations, here are a few resoruces that could be helpful:

[Big O Lecture Notes - Salisbury University](http://faculty.salisbury.edu/~ealu/COSC320/Lectures/complexity.pdf) \
[Big O cheat sheet](https://www.bigocheatsheet.com) \
[My presentation](https://nikhil0504.github.io/School-PPT/) 