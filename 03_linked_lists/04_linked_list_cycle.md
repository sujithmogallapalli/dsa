## Problem
Given head, the head of a linked list, determine if the linked list has a cycle in it.

Return true if there is a cycle in the linked list. Otherwise, return false.

## Sample
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).

## Approaches
### Approach 1 - Floyd’s Cycle Detection Algorithm (also called the Tortoise and Hare approach).
- slow pointer → moves 1 step
- fast pointer → moves 2 steps
- If there is a cycle:
  - They eventually meet. 
  - If no cycle:
    - fast reaches null.
- Time complexity - O(n), Space complexity - O(1)

### Approach 2 - Hashing Approach
- Traverse the linked list.
- Store each node reference in a HashSet.
- Before adding a node:
  - Check if it already exists in the set. 
  - If yes → cycle detected.
- If traversal ends → no cycle.
- Time complexity - O(n), Space complexity - O(n)

## Codes
### Floyd’s Cycle Detection Algorithm (also called the Tortoise and Hare approach).
```java
public boolean hasCycle(ListNode head) {
    if (head == null)
        return false;
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow == fast)
            return true;
    }
    return false;
}
```
### Pitfalls
- While loop check should be based on fast node

### Hashing Approach
```java
public boolean hasCycle(ListNode head) {
    if (head == null)
        return false;
    
    Set<ListNode> setOfNodes = new HashSet<>();
    while (head != null) {
        if (setOfNodes.contains(head))
            return true;
        setOfNodes.add(head);
        head = head.next;
    }
    return false;
}
```