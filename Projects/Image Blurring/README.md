## P2
A good starting place is to map each thread to a pixel as you have before.
 Then every thread can perform steps 2 and 3 in the diagram above
 completely independently of one another.

 Note that the array of weights is square, so its height is the same as its width.
 We refer to the array of weights as a filter, and we refer to its width with the
 variable filterWidth.

****************************************************************************

 Your homework submission will be evaluated based on correctness and speed.
 We test each pixel against a reference solution. If any pixel differs by
 more than some small threshold value, the system will tell you that your
 solution is incorrect, and it will let you try again.

 Once you have gotten that working correctly, then you can think about using
 shared memory and having the threads cooperate to achieve better performance.

****************************************************************************
 Also note that we've supplied a helpful debugging function called checkCudaErrors.
 You should wrap your allocation and copying statements like we've done in the
 code we're supplying you. Here is an example of the unsafe way to allocate
 memory on the GPU:

 cudaMalloc(&d_red, sizeof(unsigned char) * numRows * numCols);

 Here is an example of the safe way to do the same thing:

 checkCudaErrors(cudaMalloc(&d_red, sizeof(unsigned char) * numRows * numCols));

 Writing code the safe way requires slightly more typing, but is very helpful for
 catching mistakes. If you write code the unsafe way and you make a mistake, then
 any subsequent kernels won't compute anything, and it will be hard to figure out
 why. Writing code the safe way will inform you as soon as you make a mistake.
 Finally, remember to free the memory you allocate at the end of the function.
