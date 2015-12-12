# Skip list

A skip list is a variant of a linked list for sorted elements, allowing faster travel times.

![Skip list](https://upload.wikimedia.org/wikipedia/commons/thumb/8/86/Skip_list.svg/470px-Skip_list.svg.png)

The bottom layer is a basic linked list.  
Each higher layer allows for a fastest transversal of the list by skipping some values (with a probability commonly of 1/2 or 3/4).

It allows algorithms like dichotomy to be close to what one could have with an array, but does not require contiguous memory (it still requires more memory than an array, for storing all the pointers)
