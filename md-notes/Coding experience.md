#### 1. When using a **single linked list**, never move if `next == null`.
In other words:
Never let your node be `null`.
Reason:
If you do this, you will lose the ability to alter the `next` pointer of the previous node, which is null.
Solution:
First check if next pointer is null, then move the iterator. 
#### 2. When using a **single linked list** as parameter, don't alter it, use another `node` variable.
Reason:
Or you won't be able to track the whole list.
