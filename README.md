# DAY_11
REMOVE Nth Node from End of the List  


# Remove N-th Node From End of List – Java Solution

This repository contains a Java solution to remove the **N-th node from the end** of a singly linked list in one pass using the two-pointer technique.

---

## 📘 Problem Statement

Given the `head` of a linked list, remove the `n`-th node from the end of the list and return its head.

### Example:

Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]

---

## 🧠 Approach

This solution uses the **two-pointer technique**:

1. **Advance one pointer (`head`) by `n` steps.**
2. **Maintain a second pointer (`dummy`) from the start.**
3. When the first pointer reaches the end, the second pointer will be just before the node to delete.
4. **By skipping the next node, we remove the target node efficiently.**

A dummy node is used at the start to simplify edge cases, such as removing the first node.

---

## 💡 Algorithm

1. Create a dummy node pointing to the head of the list.
2. Move the `head` pointer `n` steps forward.
3. Move both `head` and `dummy` one step at a time until `head` reaches the end.
4. Update `dummy.next` to `dummy.next.next` to skip the N-th node from the end.
5. Return the updated list starting from `dummy.next`.

---

## 🧾 Java Code

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode res = new ListNode(0, head);
        ListNode dummy = res;
        for(int i = 0; i < n; i++) head = head.next;
        while(head != null) {
            head = head.next;
            dummy = dummy.next;
        }
        dummy.next = dummy.next.next;
        return res.next;
    }
}
🧪 Test Cases
Input List	n	Output List
[1, 2, 3, 4, 5]	2	[1, 2, 3, 5]
[1]	1	[]
[1, 2]	1	[1]
[1, 2]	2	[2]

🚀 Complexity Analysis
Time Complexity: O(L) where L is the length of the list (single pass).

Space Complexity: O(1) – constant extra space.
