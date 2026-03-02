## Problem
Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

## Observations
- If the head is null, return null

## Approaches
### Approach 1 - Use two pointers
- Initialize two temporary nodes slow, fast
- slow will be traversing one node at a time
- fast will be traversing two nodes at a time
- When fast reaches the end, slow will be at middle
- Time complexity - O(n), Space Complexity - O(1)
#### Pitfalls 
- Condition while traversing will be needed only on fast

### Approach 2 - Finding size and traverse through the half of the list
- Traverse through the list and store the size of the list
- Traverse through the half of the size of the list
- Return the node

## Codes
### Use two pointers
```java
public ListNode middleNode(ListNode head) {

    if (head == null)
        return null;

    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {;
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
}
```
### Finding size and traverse through the half of the list
```java
public ListNode middleNode(ListNode head) {

    if (head == null)
        return null;

    int size = 0;
    ListNode node = head;
    while(node != null) {
        size++;
        node = node.next;
    }

    if (size == 1)
        return head;

    int i = 0;
    node = head;
    while (i < size/2) {
        node = node.next;
        i++;
    }
    return node;
}
```

## New Learnings
- Using slow, fast nodes for finding middle one