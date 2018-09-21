###1. Variable-length array

Why C language doesn't support variable length array at first place? 

####Reason 1: Uncertainty in memory allocation.
Every function has it's own memory space. The size of this space is determined during compilation. If you let the size of an array to be an expression, which is calculated during excution, you can't decide how much space this function needs. If the function excutes several lines and finds out it needs a larger space, it then has to expand it's space, which envolves a bit load of work of saving the current environment.

####Reason 2: Uncertainty about multi-dimensional arrays.
We know this formula:
