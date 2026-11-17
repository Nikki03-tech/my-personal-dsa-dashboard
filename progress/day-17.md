# Day 17 — Linked Lists & Fast/Slow Pointers

**Date:** November 17, 2026  
**Language:** Python  
**Status:** COMPLETED ✅

## 1. Concepts Learned

- A Linked List is a collection of nodes connected through pointers.
- Every node contains data and a reference to the next node.
- `head` represents the first node of a linked list.
- `None` represents the end of a linked list.
- A cycle occurs when a node points back to an earlier node.
- Fast and Slow Pointers are used to detect cycles and find the middle node.
- A Slow Pointer moves one step at a time.
- A Fast Pointer moves two steps at a time.
- Floyd's Cycle Detection Algorithm uses fast and slow pointers to identify a cycle.
- Two-pointer switching can find the merge point of two linked lists.

## 2. Important Logic

### Linked List Cycle — LeetCode

```python
class Solution:
    def hasCycle(self, head):
        slow = head
        fast = head

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

            if slow is fast:
                return True

        return False
```

- Slow moves one node.
- Fast moves two nodes.
- If both pointers meet, a cycle exists.
- If fast reaches `None`, no cycle exists.

### Middle of the Linked List — LeetCode

```python
class Solution:
    def middleNode(self, head):
        slow = head
        fast = head

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

        return slow
```

- Slow moves one step.
- Fast moves two steps.
- When fast reaches the end, slow points to the middle.
- For an even number of nodes, this returns the second middle node.

### Detect a Cycle — HackerRank

```python
def has_cycle(head):
    slow = head
    fast = head

    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next

        if slow is fast:
            return True

    return False
```

- Uses Floyd's Cycle Detection Algorithm.
- Returns `True` if both pointers meet.
- Returns `False` if fast reaches the end.

### Find the Merge Point — HackerRank

```python
def findMergeNode(head1, head2):
    p1 = head1
    p2 = head2

    while p1 is not p2:
        if p1 is None:
            p1 = head2
        else:
            p1 = p1.next

        if p2 is None:
            p2 = head1
        else:
            p2 = p2.next

    return p1.data
```

- Use two pointers for the two linked lists.
- Move both pointers one node at a time.
- When a pointer reaches the end, redirect it to the other list's head.
- Continue until both pointers reach the same node.
- Return the data stored in the merge node.

## 3. Mistakes Corrected / Important Points

- Learned that a linked list is different from a normal Python list.
- Understood that `head` points to the first node.
- Learned why we check `fast and fast.next` before moving the fast pointer.
- Understood why the fast pointer moves two steps and the slow pointer moves one step.
- Learned that `is` checks whether two pointers refer to the same node, not just whether their values are equal.
- Understood why the Middle of the Linked List returns the second middle node for an even-length list.
- Learned that HackerRank Detect a Cycle uses the same Floyd's algorithm as LeetCode Linked List Cycle.
- Understood why pointers switch to the other list's head when finding the merge point.
- Learned that two different nodes can contain equal data, so comparing node identity is important.

## 4. Coding Problems Completed

| Platform | Problem | Result |
|---|---|---|
| LeetCode | [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) | Completed ✅ |
| LeetCode | [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) | Completed ✅ |
| HackerRank | [Detect a Cycle](https://www.hackerrank.com/challenges/ctci-linked-list-cycle/problem) | Completed ✅ |
| HackerRank | [Find the Merge Point of Two Joined Linked Lists](https://www.hackerrank.com/challenges/find-the-merge-point-of-two-joined-linked-lists/problem) | Completed ✅ |

## 5. Time & Space Complexity

| Problem | Time | Auxiliary Space |
|---|---|---|
| Linked List Cycle | O(n) | O(1) |
| Middle of the Linked List | O(n) | O(1) |
| Detect a Cycle | O(n) | O(1) |
| Find the Merge Point | O(m + n) | O(1) |

### Complexity Notes

- `n` = number of nodes in a linked list.
- `m` = number of nodes in the first linked list.
- `head` = first node.
- `next` = reference to the next node.
- `None` = end of the linked list.
- `slow = slow.next` moves one step.
- `fast = fast.next.next` moves two steps.
- `is` compares object identity.
- Floyd's algorithm uses O(1) auxiliary space.
- The merge-point problem assumes the two linked lists share a common node.

## 6. Mock Interview Questions & Answers

1. **What is a Linked List?**  
   A linear data structure where nodes store data and references to the next nodes.

2. **What is the Head of a Linked List?**  
   The head is the reference to the first node.

3. **What is a Cycle in a Linked List?**  
   A cycle occurs when a node points back to an earlier node instead of ending with `None`.

4. **What is Floyd's Cycle Detection Algorithm?**  
   An algorithm that uses fast and slow pointers to detect a cycle in a linked list.

5. **Why does the fast pointer move two steps?**  
   It allows the fast pointer to eventually meet the slow pointer if a cycle exists.

6. **How do we find the middle of a Linked List?**  
   Move slow one step and fast two steps. When fast reaches the end, slow points to the middle.

7. **What is the difference between `is` and `==`?**  
   `is` checks object identity, while `==` checks whether values are equal.

8. **How do we find the merge point of two linked lists?**  
   Use two pointers and switch each pointer to the other list's head after reaching the end. They eventually meet at the common node.

## 7. Key Learning

Learned how to traverse linked lists, detect cycles using Floyd's Cycle Detection Algorithm, find the middle node using fast and slow pointers, and identify the merge point using two pointers. Improved understanding of nodes, references, head pointers, None, object identity, and time and space complexity.

**Day 17 Completed! ✅**
