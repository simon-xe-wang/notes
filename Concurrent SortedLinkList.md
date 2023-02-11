

Options:
1. Coarse-grained Lock
2. Finer-grained lock (hand-over-hand)
3. Optimistic 
4. Lock-Free   
	1. could be optimized with Java RTTI 
5. Lazy - List


### Finer-grained Locking[](https://app.gitbook.com/o/-LCEQcKRz-2tEebjazNd/s/-LCEQcKSzcJ7F8hIruvI/programing-language/java/concurrency/linkedlist#finer-grained-locking)

lock 2 nodes

add:

-   1.
    
    lock former node
    

-   2.
    
    lock next node and release previous one.
    

-   3.
    
    insert a node btw previous and current one
    

Remove:

lock in same way as add

prev.next = curr.next

drawback:

block other threads which access later nodes


### Optimistic Synchronization[](https://app.gitbook.com/o/-LCEQcKRz-2tEebjazNd/s/-LCEQcKSzcJ7F8hIruvI/programing-language/java/concurrency/linkedlist#optimistic-synchronization)

to insert a node A, find a node > A

traverse without lock.

find node currA and predA and lock both nodes.

validate that predA is reachable and points to currA

the validation about the node is reachable is done by traversing from head

​

![](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LCEQcKSzcJ7F8hIruvI%2Fuploads%2Fzk2qzprFKv4YPRShEf9g%2Fimage.png?alt=media&token=629e17fb-a448-4e94-86f5-fd697a8e24d0)

​

​

### Lazy Synchronization (Logical remove)[](https://app.gitbook.com/o/-LCEQcKRz-2tEebjazNd/s/-LCEQcKSzcJ7F8hIruvI/programing-language/java/concurrency/linkedlist#lazy-synchronization-logical-remove)

In optimistic synchronization, contains() also needs to acquire locks. which is not performant.

Use a flag to mark if the node is removed or not.

validate() doesn't need to traverse the list. Just check the flag in pred and curr.

​

### Nonblocking Synchronization[](https://app.gitbook.com/o/-LCEQcKRz-2tEebjazNd/s/-LCEQcKSzcJ7F8hIruvI/programing-language/java/concurrency/linkedlist#nonblocking-synchronization)

-   treat the next pointer and the marker field as a single atomic unit.
    

-   AtomicMarkableReference
    

​

​