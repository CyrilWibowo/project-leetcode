# Linked List

## Creating a Linked List

```python
# Node class definition
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

# Create single node
node = ListNode(1)

# Create linked list from values
def create_list(values):
    dummy = ListNode(0)
    curr = dummy
    for val in values:
        curr.next = ListNode(val)
        curr = curr.next
    return dummy.next

head = create_list([1, 2, 3, 4, 5])

# Doubly linked list node
class DoublyListNode:
    def __init__(self, val=0, prev=None, next=None):
        self.val = val
        self.prev = prev
        self.next = next
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Access by index | O(n) |
| Insert at head | O(1) |
| Insert at tail | O(1) with tail pointer |
| Insert at position | O(1) with pointer, O(n) to find |
| Delete at position | O(1) with pointer, O(n) to find |
| Search | O(n) |

### Python Implementations

#### Insert at Head - O(1)

```python
def insert_head(head, val):
    new_node = ListNode(val)
    new_node.next = head
    return new_node
```

#### Insert at Tail - O(n)

```python
def insert_tail(head, val):
    new_node = ListNode(val)
    if not head:
        return new_node
    curr = head
    while curr.next:
        curr = curr.next
    curr.next = new_node
    return head
```

#### Delete Node - O(1) with reference

```python
def delete_node(node):
    # Can't delete if it's the last node
    node.val = node.next.val
    node.next = node.next.next
```

#### Delete by Value - O(n)

```python
def delete_value(head, val):
    dummy = ListNode(0, head)
    curr = dummy
    while curr.next:
        if curr.next.val == val:
            curr.next = curr.next.next
        else:
            curr = curr.next
    return dummy.next
```

#### Search - O(n)

```python
def search(head, val):
    curr = head
    index = 0
    while curr:
        if curr.val == val:
            return index
        curr = curr.next
        index += 1
    return -1
```

#### Get Length - O(n)

```python
def get_length(head):
    length = 0
    curr = head
    while curr:
        length += 1
        curr = curr.next
    return length
```

#### Reverse Linked List - O(n)

```python
def reverse(head):
    prev = None
    curr = head
    while curr:
        next_node = curr.next
        curr.next = prev
        prev = curr
        curr = next_node
    return prev
```

#### Reverse (Recursive) - O(n)

```python
def reverse_recursive(head):
    if not head or not head.next:
        return head
    new_head = reverse_recursive(head.next)
    head.next.next = head
    head.next = None
    return new_head
```

#### Detect Cycle (Floyd's Algorithm) - O(n)

```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

#### Find Cycle Start - O(n)

```python
def find_cycle_start(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            slow = head
            while slow != fast:
                slow = slow.next
                fast = fast.next
            return slow
    return None
```

#### Find Middle - O(n)

```python
def find_middle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow
```

#### Merge Two Sorted Lists - O(n + m)

```python
def merge_sorted(l1, l2):
    dummy = ListNode(0)
    curr = dummy
    while l1 and l2:
        if l1.val <= l2.val:
            curr.next = l1
            l1 = l1.next
        else:
            curr.next = l2
            l2 = l2.next
        curr = curr.next
    curr.next = l1 or l2
    return dummy.next
```

#### Remove Nth Node From End - O(n)

```python
def remove_nth_from_end(head, n):
    dummy = ListNode(0, head)
    slow = fast = dummy
    for _ in range(n + 1):
        fast = fast.next
    while fast:
        slow = slow.next
        fast = fast.next
    slow.next = slow.next.next
    return dummy.next
```

#### Check Palindrome - O(n)

```python
def is_palindrome(head):
    # Find middle
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next

    # Reverse second half
    prev = None
    while slow:
        next_node = slow.next
        slow.next = prev
        prev = slow
        slow = next_node

    # Compare halves
    left, right = head, prev
    while right:
        if left.val != right.val:
            return False
        left = left.next
        right = right.next
    return True
```

#### Intersection of Two Lists - O(n + m)

```python
def get_intersection(headA, headB):
    if not headA or not headB:
        return None
    a, b = headA, headB
    while a != b:
        a = a.next if a else headB
        b = b.next if b else headA
    return a
```

---

## What It Provides

- Dynamic size
- O(1) insertion/deletion with pointer
- No need for contiguous memory

## What It Requires

- Extra space for pointers
- Sequential access

## Good For

- Frequent insertions/deletions
- LRU cache implementation
- Representing sequences
- When size unknown

## Use When You Need

- Efficient middle insertions
- No random access needed
- Dynamic growing/shrinking
- Cycle detection (fast/slow pointers)
