## Problem
Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

## Sample
Input: head = [1,2,2,1]
Output: true

## Approaches
### Approach 1 – Fast & Slow Pointer + Reverse Second Half
- Use slow & fast pointers to find middle.
- Reverse second half in-place.
- Compare first half and reversed second half.
  - If mismatch → false.
- Time Complexity: O(n), Space Complexity: O(1)

### Approach 2 - String Conversion & Reverse Comparison (Brute Force)
- Traverse the linked list.
- Append each node value to a StringBuilder.
- Add delimiter (space) to avoid ambiguity.
- Convert to String.
- Reverse the StringBuilder.
- Compare original and reversed strings.
- If equal → Palindrome.
- Time Complexity: O(n), Space Complexity: O(n)

## Codes
### Fast & Slow Pointer + Reverse Second Half
```java
public boolean isPalindrome(ListNode head) {
    if (head == null || head.next == null) 
        return true;

    // Step 1: Find middle
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }

    // Step 2: Reverse second half
    ListNode prev = null;
    while (slow != null) {
        ListNode next = slow.next;
        slow.next = prev;
        prev = slow;
        slow = next;
    }

    // Step 3: Compare halves
    ListNode first = head, second = prev;
    while (second != null) {
        if (first.val != second.val)
            return false;
        first = first.next;
        second = second.next;
    }

    return true;
}
```
### String Conversion & Reverse Comparison (Brute Force)
```java
 public boolean isPalindrome(ListNode head) {
    StringBuilder sb = new StringBuilder();
    while (head != null) {
        sb.append(head.val);
        if (head.next != null)
            sb.append(" ");
        head = head.next;
    }
    return sb.toString().contentEquals(sb.reverse());
}
```