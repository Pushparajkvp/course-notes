# Data Structures

1. A data structure is a way of organizing data so that it can be used effectively.
1. Abstract Data Types VS Data Structures
    1. An Abstract data type is an abstraction of a data structure which provides only the interface to which the data structure must adhere to.
    1. It Does not indicate specific details about how something should be implemented or in what programming language.
    1. ![ADT](Images/ADT.jpg)
1. Computation Complexity
    1. How much time and space is needed?
    1. Big O
        1. Only cares about worst case.
        1. ![Big O](Images/bigo.jpg)
        1. Can ignore constants because n-> infinity(In real world this constant might matter)
        1. ![O(1) Constant](Images/o1.jpg)
        1. ![O(n) Linear](Images/on.jpg)
        1. ![O(n2) Quadraic](Images/on2.jpg)
        1. n + (n-1) + (n-2) ... = n(n+1)/2
        1. ![O(logn) Logarithimic](Images/ologn.jpg)
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
        1. ![Array Complexity](Images/arraycomplexity.jpg)
    1. Dynamic Arrays
        1. Dynamic arrays can grow and shrink and can have methods like add and remove
        1. ![Dynamic Array Implementation With Static Arrays](Images/dynamicarrayimpl.jpg)
1. Linked Lists
    1. Used in many lists, queue and graph implementation.
    1. Great to create circular lists.
    1. Can easily model real world objects like train.
    1. Used in separate chainging which is present in certain hashtable implementations to deal with hashing collisions.
    1. Often used in implementation of adjacentcy lists of graph.
    1. ![Linked List](Images/linkedlist.jpg)
    1. ![Doubly Linked List](Images/doublylinkedlist.jpg)
    1. ![Pros and cons](Images/dllsllprosandcons.jpg)
    1. 64 bit machine -> points use 8 bytes
    1. In Doubly linkedlist we can remove node in constant time
    1. ![Insert Singly Linkedlist](Images/insertsinglylinkedlist.jpg)
    1. ![Insert doubly Linkedlist](Images/insertdoublylinkedlist.jpg)
    1. ![Remove Sinlgy Linkedlist](Images/removesinglylinkedlist.jpg)
    1. ![Remove doubly Linkedlist](Images/removedoublylinkedlist.jpg)
    1. ![Complexity 1](Images/linkedlistcomplexity1.jpg)
    1. ![Complexity 2](Images/linkedlistcomplexity2.jpg)
1. Stack
    1. A stack is a one-ended linear data structure which models a real world stack by having 2 primary operations - push and pop
    1. Last In First Out (LIFO)
    1. Comman usage areas,
        1. Undo mechanism
        1. Compiler syntax checking for matching brackets
        1. Used behind the scenes in recursion
        1. Used in DFS
    1. ![Stack Complexity](Images/stackComplexity.jpg)
    1. ![Stack Demo](Images/stackDemo.jpg)
1. Queue
    1. A queue is a linear data structure which models real world queue by having 2 primary operations - enqueue and dequeue
    1. First In Last Out (FIFO)
    1. Enqueue = Adding = Offering
    1. Dequeue = Polling
    1. Common usage areas,
        1. Real world queue
        1. Can be used to efficeintly keep track of the x most recently added elements.
        1. Web server management
        1. Used in BFS
    1. ![Queue Demo](Images/queueDemo.jpg)
    1. ![Queue Complexity](Images/queueComplexity.jpg)
1. Heap
    1. A heap is a tree based data strucuture that satisfies the heap varient.
    1. Heap varient : If A is a parent node of B then A is ordered with respect to B for all nodes A,B in the heap.
    1. ![Heap Definition](Images/heapDef.jpg)
    1. All Heaps must be trees
    1. Some common types of heaps,
        1. Binary heap
        1. Fibonacci heap
        1. Binomial heap
        1. Pairing heap
    1. Complete Binary tree
        1. A complete binary tree is a tree in which at every level, except possibly the last is completely filled and all the nodes are as far left as possible.
        1. ![Complete Binary Tree](Images/completeBinaryTree.jpg)
        1. 2^(h+1) - 1 --> maximum number of nodes in a binary tree of height h
        1. floor(logn) --> height of binary tree given number of nodes n
        1. If the last level is half filled from left to right then it is called almost complete binary tree
        1. In a complete binary tree (n/2 + 1) to n all will be leaf nodes.
    1. Binary heap
        1. A binary heap is a binary tree that supports the heap invarient.
        1. Binary heap can be implemented using arrays.
        1. ![Binary heap representation](Images/binaryHeapRepresentation.jpg)
        1. If i is the parent node 2i+1 is it's left child and 2i+2 is it's right child (zero based)
        1. Adding an element
            1. Add to the left most and bottom most position of the complete binary tree and bubble or swim it to its right position
            1. Keep on swapping until the parent node and the inserted node does not satisfy the heap invareint
        1. Removing an element
            1. Swap the element to be removed with the last element in the complete binary tree (which happens to be the last element in the array)
            1. Check invariance and swim or bubble down by swapping with the lowest of the two child nodes
            1. In case of a tie select the left node
            1. Check the invarient to decide on whether to bubble up or bubble down
            1. Polling - O(longn) Removing - O(n)
    1. Heapify
        1. Leaf nodes satisfy the heap invareint already so don't iterate through the leaf nodes.
        1. Start from the node with largest index which is not a leaf node and sink the node.
1. Priority Queue
    1. Priority queues are implemented using Heaps
    1. Priority queues does not allow null values because they cannot be compared.
    1. A priority queue is an Abstract Data Type (ADT) that operates similar to normal queue except that each element has a certain priority. The priority of the element in the priority queue determine the order in which elements are removed from the priority queue.
    1. Priority queues only supports comparable data, meaning data inserted into the priority queue must be able to be ordered in some way either from least to greatest or gratest to least.
    1. Common usages
        1. Certain implementations of Dijkstra's algo
        1. Anytime we need to dynamically fetch the "next best" or "next worst" element.
        1. Used in huffman coding (Lossless data compression)
        1. Best First Search such as A* use heaps to grab the next most promising node.
        1. Used in minimum spanning tree algo
    1. ![PQ with Binary heap complexity](Images/PQBinHeapComplexity.jpg)
    1. ![PQ with Binary heap complexity 2](Images/PQBinHeapComplexisty2.jpg)
    1. Turning Min PQ to Max PQ
        1. This can be done by negating the comparable interface
        1. Another method is to negate the number before insertion and negate again during polling
