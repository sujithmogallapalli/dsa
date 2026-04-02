## Problem
Given the head of a singly linked list, group all the nodes with odd indices together 
followed by the nodes with even indices, and return the reordered list.

## Sample
Input: head = [1,2,3,4,5]
Output: [1,3,5,2,4]

## Observations
- If the size is 0, 1 or 2 then we can return head directly

## Approaches
### Approach 1 – Pointer Rewiring / List Partitioning
- Handle edge case:
    - If list has 0 or 1 node → return head.
- Initialize:
    - `odd = head`
    - `even = head.next`
    - `evenHead = even` (store start of even chain)
- While `even != null && even.next != null`:
    - Link next odd:
      odd.next = even.next
    - Move odd forward
    - Link next even:
      even.next = odd.next
    - Move even forward
- After loop:
    - Attach even chain → `odd.next = evenHead`
- Return head.
- Time Complexity: O(n), Space Complexity: O(1)

## Codes
### Pointer Rewiring / List Partitioning
```java
public ListNode oddEvenList(ListNode head) {

    if (head == null || head.next == null)
        return head;

    ListNode odd = head;
    ListNode even = head.next;
    ListNode evenHead = even;

    while (even != null && even.next != null) {
        odd.next = even.next;
        odd = odd.next;

        even.next = odd.next;
        even = even.next;
    }

    odd.next = evenHead;

    return head;
}
```

## New Learning
- Odd even index partitioning