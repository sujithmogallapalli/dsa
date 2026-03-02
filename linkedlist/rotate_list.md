## Problem
- Given the head of a linked list, rotate the list to the right by k places.

## Observations
- if k = 0, head is null, size is 1 (head.next = null) return head

## Approaches
### Approach 1 – Circular Link + Break Point
- Step 1: Traverse list to:
    - Find length.
    - Reach last node (tail).
- Step 2: Normalize rotations:
    - k = k % length
    - If k == 0 → return head.
- Step 3: Find new tail:
    - Move (length - k - 1) steps from head.
    - newTail.next becomes new head.
- Step 4: Make list circular:
    - tail.next = head
- Step 5: Break circle:
    - newTail.next = null
- Return new head.
- Time Complexity: O(n), Space Complexity: O(1)
#### New Learnings
- Avoiding prev node with calculation of correct steps

### Approach 2 – Two Pointer Fixed Gap (Rotation)
- Step 1: Traverse list to calculate length.
- Step 2: Normalize k using modulo.
- Step 3: Move fast pointer k steps ahead.
- Step 4: Move both slow and fast together:
    - When fast reaches last node,
      slow will be at new tail.
- Step 5: Rewire:
    - newHead = slow.next
    - slow.next = null
    - fast.next = old head
- Return newHead.
- Time Complexity: O(n), Space Complexity: O(1)

## Codes
### Circular Link + Break Point
```java
public ListNode rotateRight(ListNode head, int k) {

    if (head == null || head.next == null || k == 0)
        return head;

    // Step 1: Find length and last node
    int size = 1;
    ListNode tail = head;

    while (tail.next != null) {
        size++;
        tail = tail.next;
    }

    // Step 2: Normalize k
    k = k % size;
    if (k == 0)
        return head;

    // Step 3: Find new tail (size - k - 1 steps)
    int stepsToNewTail = size - k - 1;
    ListNode newTail = head;

    for (int i = 0; i < stepsToNewTail; i++) {
        newTail = newTail.next;
    }

    // Step 4: Rewire pointers
    ListNode newHead = newTail.next;
    newTail.next = null;
    tail.next = head;

    return newHead;
}
```
### Two Pointer Fixed Gap Technique (Rotation Variant)
```java
public ListNode rotateRight(ListNode head, int k) {

    if (head == null || head.next == null || k == 0)
        return head;

    // Step 1: Calculate length
    int length = 0;
    ListNode curr = head;

    while (curr != null) {
        length++;
        curr = curr.next;
    }

    // Step 2: Normalize k
    k = k % length;
    if (k == 0)
        return head;

    // Step 3: Create k-gap
    ListNode fast = head;
    for (int i = 0; i < k; i++) {
        fast = fast.next;
    }

    ListNode slow = head;

    // Step 4: Move together
    while (fast.next != null) {
        slow = slow.next;
        fast = fast.next;
    }

    // Step 5: Rewire pointers
    ListNode newHead = slow.next;
    slow.next = null;
    fast.next = head;

    return newHead;
}
```