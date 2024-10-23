
# Algorithm Templates in Swift

This repository contains Swift implementations of common algorithmic patterns used in common interview and leetcode questions. These templates serve as a foundation for solving various algorithmic problems efficiently.

---

## Table of Contents

- [Two Pointers](#two-pointers)
- [Sliding Window](#sliding-window)
- [Prefix Sum](#prefix-sum)


---

## Two Pointers

### 1. Single Input, Opposite Ends

This pattern uses two pointers starting from opposite ends of the array and moving towards each other based on certain conditions.

```swift
func twoPointersSingleInput(_ arr: [Int]) -> Int {
    var left = 0
    var right = arr.count - 1
    var ans = 0

    while left < right {
        // Do some logic here with left and right
        // Example condition (replace with actual condition)
        if /* CONDITION */ {
            left += 1
        } else {
            right -= 1
        }
    }

    return ans
}
```

---

### 2. Two Inputs, Exhaust Both

This pattern uses two pointers to traverse two separate arrays until both are fully processed.

```swift
func twoPointersTwoInputs(_ arr1: [Int], _ arr2: [Int]) -> Int {
    var i = 0
    var j = 0
    var ans = 0

    while i < arr1.count && j < arr2.count {
        // Do some logic here
        // Example condition (replace with actual condition)
        if /* CONDITION */ {
            i += 1
        } else {
            j += 1
        }
    }

    while i < arr1.count {
        // Do logic for remaining elements in arr1
        // Example logic (replace with actual logic)
        i += 1
    }

    while j < arr2.count {
        // Do logic for remaining elements in arr2
        // Example logic (replace with actual logic)
        j += 1
    }

    return ans
}
```

---

## Sliding Window

This pattern maintains a window that satisfies certain conditions while traversing the array.

```swift
func slidingWindow(_ arr: [Int]) -> Int {
    var left = 0
    var ans = 0
    var curr = 0

    for right in 0..<arr.count {
        // Add arr[right] to curr
        // Example logic (replace with actual logic)
        curr += arr[right]

        // Adjust the window if the condition is broken
        while /* WINDOW_CONDITION_BROKEN */ {
            // Remove arr[left] from curr
            // Example logic (replace with actual logic)
            curr -= arr[left]
            left += 1
        }

        // Update ans based on the current window
        // Example logic (replace with actual logic)
        ans = max(ans, curr)
    }

    return ans
}
```

---

## Prefix Sum

This pattern creates a prefix sum array where each element at index `i` represents the sum of elements from index `0` to `i` in the original array.

```swift
func buildPrefixSum(_ arr: [Int]) -> [Int] {
    guard !arr.isEmpty else { return [] }
    
    var prefix = Array(repeating: 0, count: arr.count)
    prefix[0] = arr[0]

    for i in 1..<arr.count {
        prefix[i] = prefix[i - 1] + arr[i]
    }

    return prefix
}
```

---

## Efficient String Building
This pattern efficiently builds a string from an array of characters.

```swift
func buildString(from arr: [Character]) -> String {
    return String(arr)
}
```

Another common pattern for editing a string is to convert it to an array of characters, make the necessary changes, and then convert it back to a string. Swift is sometimes hard to edit strings directly because characters can be diferent sizes so you cant directly index into them. This allows you to edit strings as you would in other lauanges using index nodation.

```swift
func editString(_ str: String) -> String {
    var arr = Array(str)
    // Make changes to arr
    return String(arr)
}
```

---

## Linked List: Fast and Slow Pointer

This pattern uses two pointers to traverse the linked list at different speeds.

```swift
class ListNode {
    var val: Int
    var next: ListNode?
    init(_ val: Int) {
        self.val = val
        self.next = nil
    }
}

func fastAndSlowPointer(_ head: ListNode?) -> Int {
    var slow = head
    var fast = head
    var ans = 0

    while fast != nil && fast?.next != nil {
        // do logic
        slow = slow?.next
        fast = fast?.next?.next
    }

    return ans
}
```

--- 
## Reversing a Linked List

This pattern reverses a linked list.

```swift
func reverseLinkedList(_ head: ListNode?) -> ListNode? {
    var curr = head
    var prev: ListNode? = nil
    while curr != nil {
        let nextNode = curr?.next
        curr?.next = prev
        prev = curr
        curr = nextNode
    }

    return prev
}
```

---

## Find Number of Subarrays that Fit an Exact Criteria
This pattern finds the number of subarrays that fit an exact criteria using a hash map.

```swift
func findSubarrays(_ arr: [Int], _ k: Int) -> Int {
    var counts = [Int: Int]()
    counts[0] = 1
    var ans = 0
    var curr = 0

    for num in arr {
        // do logic to change curr
        ans += counts[curr - k, default: 0]
        counts[curr, default: 0] += 1
    }

    return ans
}
```

---

## Monotonic Increasing Stack
This pattern maintains a monotonic increasing stack. A monotonic stack is a stack that either only increases or only decreases.

```swift
func monotonicIncreasingStack(_ arr: [Int]) -> Int {
    var stack = [Int]()
    var ans = 0

    for num in arr {
        // for monotonic decreasing, just flip the > to <
        while !stack.isEmpty && stack.last! > num {
            // do logic
            stack.removeLast()
        }

        stack.append(num)
    }

    return ans
}
```
> **Note:** The same logic can be applied to maintain a monotonic queue.

---

## Binary Tree: DFS (Recursive)

This pattern performs a depth-first search on a binary tree using recursion.

```swift
class TreeNode {
    var val: Int
    var left: TreeNode?
    var right: TreeNode?
    init(_ val: Int) {
        self.val = val
        self.left = nil
        self.right = nil
    }
}

func dfsRecursive(_ root: TreeNode?) -> Int {
    guard let root = root else {
        return 0
    }

    var ans = 0
    // do logic
    _ = dfsRecursive(root.left)
    _ = dfsRecursive(root.right)
    return ans
}
```

## Binary Tree: DFS (Iterative)
This pattern performs a depth-first search on a binary tree using an iterative approach with a stack.
```swift
func dfsIterative(_ root: TreeNode?) -> Int {
    guard let root = root else {
        return 0
    }

    var stack = [TreeNode]()
    stack.append(root)
    var ans = 0

    while !stack.isEmpty {
        let node = stack.removeLast()
        // do logic
        if let left = node.left {
            stack.append(left)
        }
        if let right = node.right {
            stack.append(right)
        }
    }

    return ans
}
```

## Binary Tree: BFS
This pattern performs a breadth-first search on a binary tree using a queue.
```swift
func bfs(_ root: TreeNode?) -> Int {
    guard let root = root else {
        return 0
    }

    var queue = [TreeNode]()
    queue.append(root)
    var ans = 0

    while !queue.isEmpty {
        let currentLength = queue.count
        // do logic for current level

        for _ in 0..<currentLength {
            let node = queue.removeFirst()
            // do logic
            if let left = node.left {
                queue.append(left)
            }
            if let right = node.right {
                queue.append(right)
            }
        }
    }

    return ans
}
``` 

---



---

## Notes

- **ARRAY MUTABILITY:** If you need to modify the input arrays within the functions, consider using `var` instead of `let` for parameters or make copies inside the function.
- **EDGE CASES:** Always consider edge cases, such as empty arrays, when implementing these patterns in real-world scenarios.
