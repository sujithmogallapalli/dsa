## Problem
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

## Sample
![img_1.png](img_1.png)
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]

## Observations
- If all the elements are matches with given value, return null

## Approaches
### Approach 1 – Dummy Node + Single Traversal
- Create a dummy node (`first`) and point it to head.
- Maintain two pointers:
    - `prev` → previous node
    - `curr` → current node
- Traverse the list:
    - If `curr.val == target`:
        - Skip node → `prev.next = curr.next`
    - Else:
        - Move `prev` forward
    - Always move `curr` forward
- Return `dummy.next` (new head).
- Time Complexity: O(n), Space Complexity: O(1)

### Approach – Recursive Deletion (Post-order Processing)
- Base Case:
    - If `head == null` → return null.
- Recursive Step:
    - Recursively process the rest of the list:
      `head.next = removeElements(head.next, val)`
- Decision Step (while backtracking):
    - If `head.val == val`
      → skip current node → return `head.next`
    - Else
      → keep node → return `head`
- Time Complexity: O(n), Space Complexity: O(n)   // recursion stack

## Codes
### Dummy Node + Single Traversal
```java
public ListNode removeElements(ListNode head, int val) {

    if (head == null)
        return null;

    // Dummy node to handle head deletion safely
    ListNode dummy = new ListNode(0);
    dummy.next = head;

    ListNode prev = dummy;
    ListNode curr = head;

    while (curr != null) {
        if (curr.val == val) {
            prev.next = curr.next;  // Remove node
        } else {
            prev = curr;            // Move prev only if not deleted
        }
        curr = curr.next;
    }

    return dummy.next;
}
```
### Recursive Deletion (Post-order Processing)
```java
public ListNode removeElements(ListNode head, int val) {

    if (head == null)
        return null;

    // Recursively process rest of the list
    head.next = removeElements(head.next, val);

    // Decide whether to keep current node
    if (head.val == val)
        return head.next;

    return head;
}
```
## Pitfalls
- Handling the deletion when the nodes are at starting position.

## New Learning
- Approach of pointing dummy node to head for safe deletion of starting nodes instead of separate loop
