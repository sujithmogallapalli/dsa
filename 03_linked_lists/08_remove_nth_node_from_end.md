## Problem
Given the head of a linked list, remove the nth node from the end of the list and return its head.

## Sample
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]

## Approaches
### Approach 1 – Two Pointer Fixed Gap Technique(Single Pass Removal)
- Create a dummy node pointing to head (handles head deletion safely).
- Initialize:
    - `fast = dummy`
    - `slow = dummy`
- Move `fast` pointer `n + 1` steps ahead.
    - This creates a fixed gap of `n` between `slow` and the target node.
- Move both pointers together until `fast` becomes null.
- Now:
    - `slow.next` is the node to remove.
- Delete node:
    - `slow.next = slow.next.next`
- Return `dummy.next`.
- Time Complexity: O(n), Space Complexity: O(1)

### Approach 2 – Length Calculation + Index Deletion
- Traverse the list once to calculate total length.
- Compute target index:
  index = length - n
- Use dummy node to simplify head deletion.
- Traverse again up to (index) position.
- Remove node:
  prev.next = prev.next.next
- Return dummy.next.
- Time Complexity: O(n), Space Complexity: O(1)


## Codes
### Two Pointer Fixed Gap Technique(Single Pass Removal)
```java
public ListNode removeNthFromEnd(ListNode head, int n) {

    ListNode dummy = new ListNode(0);
    dummy.next = head;

    ListNode fast = dummy;
    ListNode slow = dummy;

    // Move fast n+1 steps ahead
    for (int i = 0; i <= n; i++) {
        fast = fast.next;
    }

    // Move both until fast reaches end
    while (fast != null) {
        fast = fast.next;
        slow = slow.next;
    }

    // Remove target node
    slow.next = slow.next.next;

    return dummy.next;
}
```

### Length Calculation + Index Deletion
```java
public ListNode removeNthFromEnd(ListNode head, int n) {

    // Step 1: Calculate length
    int length = 0;
    ListNode temp = head;
    while (temp != null) {
        length++;
        temp = temp.next;
    }

    // Step 2: Create dummy node
    ListNode dummy = new ListNode(0);
    dummy.next = head;

    // Step 3: Find node before target
    int targetIndex = length - n;
    ListNode prev = dummy;

    while (targetIndex-- > 0) {
        prev = prev.next;
    }

    // Step 4: Remove target node
    prev.next = prev.next.next;

    return dummy.next;
}
```

## New Learning
- Gap technique