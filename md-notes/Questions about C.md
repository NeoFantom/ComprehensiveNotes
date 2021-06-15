### 1. Variable-length array

Why C language doesn't support variable length array at first place? 

#### Reason 1: Uncertainty in memory allocation.
Every function has it's own memory space. The size of this space is determined during compilation. If you let the size of an array to be an expression, which is calculated during excution, you can't decide how much space this function needs. If the function excutes several lines and finds out it needs a larger space, it then has to expand it's space, which envolves a bit load of work of saving the current environment.

#### Reason 2: Uncertainty about multi-dimensional arrays.
We know this about arrays in C:
```C
int x[3] = {1, 2, 3};
// Now x[1] is actually translated to *(x + 1) in assembly language
printf("%d", x[1])      // 2
printf("%d", *(x + 1))  // 2
```
Similarly for 2-d arrays in C, we have:
```C
int array[3][2] = {{1, 2}, {3, 4}, {5, 6}}；
```
Now `array[2][1]` is translated to `*(*(array + 2 * 3) + 1)`

So `array[i][j]` is actually `*(*(array + i * row_length) + j)`

But if we allow variable length array, we have a problem.

Suppose we can write:
```C
array = array[4][5]
```
Now where is `array[2][1]` stored?

More specifically, if we calculate `array[i][j]` by `*(*(array + i * row_length) + j)`, what is the `row_length`?

#### Conclusion: You need a list!
All problem said above, and all others that I didn't mention, can be solved by some methods. But try it, then you'll find you need a variable to store array's length, and you need to support memory expanding... Finally, you end up with implementing a list structure, which I believe you have learned in Data Structure. That is something too complicated for a bottom layer implementation.
