# Data Structures

1. A data structure is a way of organizing data so that it can be used effectively.
1. Abstract Data Types VS Data Structures
    1. An Abstract data type is an abstraction of a data structure which provides only the interface to which the data structure must adhere to.
    1. It Does not indicate specific details about how something should be implemented or in what programming language.
    1. ![ADT](images/ADT.jpg)
1. Computation Complexity
    1. How much time and space is needed?
    1. Big O
        1. Only cares about worst case.
        1. ![Big O](images/bigo.jpg)
        1. Can ignore constants because n-> infinity(In real world this constant might matter)
        1. ![O(1) Constant](images/o1.jpg)
        1. ![O(n) Linear](images/on.jpg)
        1. ![O(n2) Quadraic](images/on2.jpg)
        1. n + (n-1) + (n-2) ... = n(n+1)/2
        1. ![O(logn) Logarithimic](images/ologn.jpg)
        1. Multiply the loops on different levels and add the loops on the same level
        1. Examples
            1. Finding all subsets of a set -> O(2^n)
            1. Finding all permutations of a String -> O(n!)
            1. Merge Sort -> O(nlogn)
            1. Iterating a matrix -> O(nm)
1. Arrays
    1. Static Arrays
        1. A static array is a fixed length container containing n elements indexable from the range [0,n-1]
        1. Each slot/index in the array can be referenced with a number
        1. Contigous chunks of memory
        1. When and where is static array used?
            1. Storing and accessing sequential data
            1. Temp storing objects
            1. Used as buffers for IO
            1. Lookup tables and inverse lookup tables
            1. To return multiple values from a function
            1. Used in DP to cache answers for sub problems
        1. ![Array Complexity](images/arraycomplexity.jpg)
    1. Dynamic Arrays
        1. Dynamic arrays can grow and shrink and can have methods like add and remove
        1. ![Dynamic Array Implementation With Static Arrays](images/dynamicarrayimpl.jpg)
        1. 