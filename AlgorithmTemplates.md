
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

## Notes

- **PLACEHOLDERS:** Replace `/* CONDITION */` and `/* WINDOW_CONDITION_BROKEN */` with actual conditions based on your specific problem.
- **ARRAY MUTABILITY:** If you need to modify the input arrays within the functions, consider using `var` instead of `let` for parameters or make copies inside the function.
- **EDGE CASES:** Always consider edge cases, such as empty arrays, when implementing these patterns in real-world scenarios.

Feel free to customize these templates further based on your specific requirements!

