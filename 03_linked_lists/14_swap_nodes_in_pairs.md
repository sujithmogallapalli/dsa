## Problem
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

## Sample
Input: head = [1,2,3,4]
Output: [2,1,4,3]

## Approaches
### Approach 1 – Pairwise Pointer Rewiring
- Step 1: Create dummy node pointing to head.
- Step 2: Use prev pointer to track node before pair.
- Step 3: While two nodes exist:
    - first = prev.next
    - second = first.next
    - Rewire:
      first.next = second.next
      second.next = first
      prev.next = second
- Step 4: Move prev to first (end of swapped pair).
- Step 5: Return dummy.next.
- Time Complexity: O(n), Space Complexity: O(1)

### Approach 2 – Recursive Pair Reversal
- Step 1: Base Case:
    - If list has 0 or 1 node → return head.
- Step 2: Identify second node:
    - second = head.next
- Step 3: Recursively swap remaining list:
    - head.next = swapPairs(second.next)
- Step 4: Reverse current pair:
    - second.next = head
- Step 5: Return second (new head of this pair).
- Time Complexity: O(n), Space Complexity: O(n)  // recursion stack

## Codes
### Pairwise Pointer Rewiring
```java
public ListNode swapPairs(ListNode head) {

    if (head == null || head.next == null)
        return head;

    ListNode dummy = new ListNode(0);
    dummy.next = head;

    ListNode prev = dummy;

    while (prev.next != null && prev.next.next != null) {

        ListNode first = prev.next;
        ListNode second = prev.next.next;

        // Swap
        first.next = second.next;
        second.next = first;
        prev.next = second;

        // Move prev to next pair
        prev = first;
    }

    return dummy.next;
}
```
### Recursive Pair Reversal
```java
public ListNode swapPairs(ListNode head) {

    if (head == null || head.next == null)
        return head;

    ListNode second = head.next;

    head.next = swapPairs(second.next);
    second.next = head;

    return second;
}
```

## New Learnings
- Traversal technique with recursion to skip one node