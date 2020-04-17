#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a)
The run time analysis for this one is **O(n)**

- In the while loop, **n** is being multiply by itself thrice, so normally that would be **n^3**
    - e.g.: (1 ** 3) == 1 (2 ** 3) == 8, (3 ** 3) == 27
- However, in the next line, n is being increased by n x n which means every time a loop runs, a is being increased exponentially as well by n^2

The formula of this can be written as below:

    ```
    f(n) = (n * n * n) / a + (n * n)
    ```
- since we're looking at the big picture, we can opt **a** out of the equation and the formula will be

    ```
    f(n) = n

    ```

--------

b)
The run time analysis for this one is **O(n^2)**

- This is because there are two loops running in two layers of this function
    - The first layer is for loop where it loops over **range(n)**
    - The second layer is while loop where it check while j is less than **n**

The formula of this can be written as below:

    ```
    f(n) = n * n
    ```
--------
    
c)
The run time analysis for this one is **O(log n)**

- This is a recursive function where bunnies = n, is being used once which its number decrease in each recursion

    ```
    f(n) = 2 + log(n) -1
         = 2 + 
    ```

## Exercise II

In this exercise, if we run the algorithm by linear search:
    
    - This would mean every **nth** floor, we drop an egg by each storey we ascend
    
    - we would drop **nth** egg to know which floor is floor **f** when the egg breaks
    
    - for instance if we have 10th story, and the f is at 5th floor, it would take 4 egg drops and 1 broken egg to find out what is the breaking point

    - the best case scenario of this is if f is at the first floor

If we decide to use binary search:
    
    - We would go to the middle level of the building and throw the 1st egg to find out if it breaks
        
        - if it does not break, we would move up by half of the remain upper floors to throw the 2nd egg. If it still do not break, we repeat the process until we find the break point
            
        
        - Vice versa, if the 1st egg breaks, we would then have to find precisely what is the first floor where the egg would start to break by move down to the lower floors by half to throw our second eggs and see if it breaks

    - if we have the same 10th storey as the previous linear search, and 5th floor is the break point, it may seem as if we found that the 5th floor is the break point but in reality it means we would have to test out at which floor would the egg break and not break
        
        - that means the experiment has to continue. We would have to go to the half point of 5th floor, which is 3rd floor to drop the egg. if the egg breaks, it means we have to go to the lower floor, which is the second floor and the 1st floor. **That would take maximum 3 broken eggs and 1 egg drop**

        - If it goes the other way (the egg does not break at 3rd floor, then we would have to go up to the 4th floor to experiment whether it would break.
            - if it does break, then the f point is at 4th floor
            - if it does not break, then the f point is at the 5th floor
            - This would take maximum of 2 egg drops and 1 broken eggs
    
This means binary search would be more efficient than linear search to find 2 consecutive floors where one is where the egg would not break while the other is where the egg would break

Pseudo Code
-------------

egg drop = 0
egg break = 0
storey = list(range(0, n-1))
f = 0
notbreak_and_breakfloors = [0,0]

while breakpoint f equal to 0
    mid floor = (n/2)
    lower floor = 1st floor to mid floor
    upper floor = mid floor to upper floor

    walk/elevator up to mid floor

    drop the 1st egg

    if the first egg break
        add 1 to egg break 
        notbreak_and_breakfloors[1] = this floor
        assign new ==> mid floor ==> mid floor + upperfloor / 2
        move to the upper floor
        back to the loop
    if the first egg do not break
        add 1 to the egg drop
         assign new ==> mid floor ==> mid floor / 2
        go the lower floor
        
repeat until we find 2 consecutive floors where the egg breaks or do not break to find the true end point
        
    