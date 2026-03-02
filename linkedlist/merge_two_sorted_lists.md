## Problem
You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

## Approaches
### Approach 1 – Two Pointer Merge Pattern
- Create dummy node.
- Maintain pointer `curr`.
- Traverse both lists:
    - Attach smaller node to `curr.next`.
    - Move corresponding pointer.
    - Move `curr`.
- Attach remaining nodes.
- Return dummy.next.
- Time Complexity: O(n + m), Space Complexity: O(1)

### Approach 2 – Recursive Merge
- Base Case:
    - If one list is null → return the other.
- Compare list1.val and list2.val:
    - Smaller node becomes current.
    - Recursively set its next pointer.
- Return selected node.
- Time Complexity: O(n + m), Space Complexity: O(n + m)  // recursion stack

## Codes
### Two Pointer Merge Pattern
```java
public ListNode mergeTwoLists(ListNode list1, ListNode list2) {

    ListNode dummy = new ListNode(-1);
    ListNode curr = dummy;

    while (list1 != null && list2 != null) {

        if (list1.val <= list2.val) {
            curr.next = list1;
            list1 = list1.next;
        } else {
            curr.next = list2;
            list2 = list2.next;
        }

        curr = curr.next;
    }

    // Attach remaining list
    curr.next = (list1 != null) ? list1 : list2;

    return dummy.next;
}
```
### Recursive Merge
```java
public ListNode mergeTwoLists(ListNode list1, ListNode list2) {

    if (list1 == null) return list2;
    if (list2 == null) return list1;

    if (list1.val <= list2.val) {
        list1.next = mergeTwoLists(list1.next, list2);
        return list1;
    } else {
        list2.next = mergeTwoLists(list1, list2.next);
        return list2;
    }
}
```