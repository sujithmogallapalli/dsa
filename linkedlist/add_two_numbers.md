## Problem
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

## Approaches
### Approach 1 – Iterative Addition with Carry (Optimal)
- Create dummy node to build result list.
- Initialize carry = 0.
- Traverse both lists until both are null.
- For each position:
    - Take values (0 if null).
    - Compute sum = val1 + val2 + carry.
    - Update carry = sum / 10.
    - Create new node with sum % 10.
- After loop:
    - If carry > 0, add new node.
- Return dummy.next.
- Time Complexity: O(n), Space Complexity: O(n)

### Approach 2 – Recursive Addition with Carry
- Base Case:
    - If both lists are null and carry is 0 → return null.
- Extract values (0 if node is null).
- Compute sum = val1 + val2 + carry.
- Create node with sum % 10.
- Recursively call for next nodes with carry = sum / 10.
- Link current node to recursive result.
- Return current node.
- Time Complexity: O(max(n, m)), Space Complexity: O(max(n, m))  // recursion stack

## Codes
### Iterative Addition with Carry (Optimal)
```java
public ListNode addTwoNumbers(ListNode l1, ListNode l2) {

    ListNode dummy = new ListNode(0);
    ListNode curr = dummy;

    int carry = 0;

    while (l1 != null || l2 != null) {

        int val1 = (l1 != null) ? l1.val : 0;
        int val2 = (l2 != null) ? l2.val : 0;

        int sum = val1 + val2 + carry;
        carry = sum / 10;

        curr.next = new ListNode(sum % 10);
        curr = curr.next;

        if (l1 != null) l1 = l1.next;
        if (l2 != null) l2 = l2.next;
    }

    if (carry > 0) {
        curr.next = new ListNode(carry);
    }

    return dummy.next;
}
```

### Recursive Addition with Carry
```java
public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    return add(l1, l2, 0);
}

private ListNode add(ListNode l1, ListNode l2, int carry) {

    if (l1 == null && l2 == null && carry == 0)
        return null;

    int val1 = (l1 != null) ? l1.val : 0;
    int val2 = (l2 != null) ? l2.val : 0;

    int sum = val1 + val2 + carry;

    ListNode node = new ListNode(sum % 10);

    node.next = add(
        (l1 != null) ? l1.next : null,
        (l2 != null) ? l2.next : null,
        sum / 10
    );

    return node;
}
```