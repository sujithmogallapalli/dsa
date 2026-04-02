## Problem
- Given the head of a sorted linked list, delete all duplicates such that each element appears only once.
- Return the linked list sorted as well.

## Sample
Input: head = [1,1,2]
Output: [1,2]

## Approaches
### Approach 1 – Single Traversal
- If list is empty or has one node → return head.
- Maintain two pointers:
    - `prev` → last unique node
    - `curr` → current node being checked
- Traverse the list:
    - If `curr.val == prev.val`
      → skip duplicate → `prev.next = curr.next`
    - Else
      → move `prev` forward
    - Always move `curr` forward
- Return original head.
- Time Complexity: O(n), Space Complexity: O(1)

## Codes
### Single Traversal
```java
public ListNode deleteDuplicates(ListNode head) {

    if (head == null || head.next == null)
        return head;

    ListNode prev = head;
    ListNode curr = head.next;

    while (curr != null) {
        if (curr.val == prev.val) {
            prev.next = curr.next;   // remove duplicate
        } else {
            prev = curr;             // move prev only when unique
        }
        curr = curr.next;
    }

    return head;
}
```