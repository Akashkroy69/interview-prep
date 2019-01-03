
# Backtracking/Exhaustive search


## Paradigm:

1. Same as recursion
    - Manually change problem by performing first step
    - Call recursive function for the remaining problem
2. Check if we have reached a valid result
    - If yes, print/store result
3. **This is new**: Undo the changes made in step 1

## When to use this:

Use backtracking/exhaustive search when you either have to go back or when the problem may have more than 1 result and you want all of them.

## Problems:

1. N Queens (Leetcode 51)
2. Permutations of a given string (Leetcode 46)