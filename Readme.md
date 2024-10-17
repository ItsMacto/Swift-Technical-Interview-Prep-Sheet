
# Swift Technical Interview Preparation

Preparing for a technical interview in Swift requires a solid understanding of data structures, algorithms, and the language's unique features. This guide provides an overview of essential data structures and algorithms, complete with Swift code snippets and explanations to help you master the concepts needed to excel in your interviews.

## Table of Contents

1. [Arrays in Swift](#arrays-in-swift)
    - [Creating Arrays](#creating-arrays)
    - [Accessing Elements](#accessing-elements)
    - [Modifying Arrays](#modifying-arrays)
    - [Iterating Over Arrays](#iterating-over-arrays)
    - [Array Properties and Methods](#array-properties-and-methods)
    - [Slicing Arrays](#slicing-arrays)
    - [Combining Arrays](#combining-arrays)
    - [Sorting Arrays](#sorting-arrays)
    - [Functional Programming with Arrays](#functional-programming-with-arrays)
    - [Multi-Dimensional Arrays](#multi-dimensional-arrays)
    - [Copying Arrays](#copying-arrays)
    - [Common Array Operations](#common-array-operations)
2. [Sets in Swift](#sets-in-swift)
    - [Creating Sets](#creating-sets)
    - [Accessing Elements](#accessing-elements)
    - [Modifying Sets](#modifying-sets)
    - [Set Properties and Methods](#set-properties-and-methods)
    - [Common Operations](#common-operations)
    - [Set Intersection, Union, and Difference](#set-intersection-union-and-difference)
    - [Set Membership and Comparison](#set-membership-and-comparison)
    - [Using Sets with Custom Types](#using-sets-with-custom-types)
    - [Direct access array as a set](#direct-access-array-as-a-set)
3. [Dictionaries in swift](#Dictionaries-in-swift)
    - [Accessing Elements](#accessing-elements)
    - [Modifying Dictionaries](#modifying-dictionaries)
    - [Dictionary Properties and Methods](#dictionary-properties-and-methods)
    - [Common Operations](#common-operations)
    - [Merging Dictionaries](#merging-dictionaries)
    - [Using Dictionaries with Custom Types](#using-dictionaries-with-custom-types)
4. [Stacks in Swift](#stack-in-swift)
    - [Creating a Stack](#creating-a-stack)
    - [Push and Pop Operations](#push-and-pop-operations)
    - [Peek Operation](#peek-operation)
5. [Queues in Swift](#queues-in-swift)
    - [Creating a Queue](#creating-a-queue)
    - [Enqueue and Dequeue Operations](#enqueue-and-dequeue-operations)
    - [Peek Operation](#peek-operation)
6. [Heap/Priority Queue in Swift](#heap-priority-queue-in-swift)
    - [Creating a Heap](#creating-a-heap)
    - [Inserting Elements](#inserting-elements)
    - [Removing Elements](#removing-elements)
    - [Min and Max Lookup](#Min-and-Max-Lookup)



---

## Arrays in Swift

Arrays are one of the fundamental data structures in Swift, providing an ordered collection of elements. They are used extensively in technical interviews to test understanding of data manipulation and algorithm implementation.

### Creating Arrays

#### Empty Array

```swift
// Using type annotation
var numbers: [Int] = []

// Using initializer syntax
var moreNumbers = [Int]()

// Swift can infer the type if initial values are provided
var inferredNumbers = [1, 2, 3]
```
> **Note:** It is important to know the basic data types in swift and immutability (var vs let) before working with arrays.

#### Array with Default Values

```swift
// Creates an array with 5 zeros
let zeros = Array(repeating: 0, count: 5) // [0, 0, 0, 0, 0]
```

### Accessing Elements

#### Subscript Syntax

```swift
let firstNumber = numbers[0]
```

#### Safe Access

```swift
if let firstNumber = numbers.first {
    print("First number is \(firstNumber)")
} else {
    print("Array is empty")
}
```

### Modifying Arrays

#### Append Elements

```swift
numbers.append(4) // Adds 4 at the end
```

#### Insert Elements

```swift
numbers.insert(0, at: 0) // Inserts 0 at index 0
```

#### Remove Elements

```swift
let removedNumber = numbers.remove(at: 2) // Removes element at index 2
```

#### Update Elements

```swift
numbers[1] = 10 // Updates the element at index 1 to 10
```

### Iterating Over Arrays

#### For-In Loop

```swift
for number in numbers {
    print(number)
}
```

#### forEach Method

```swift
numbers.forEach { number in
    print(number)
}
```

#### Enumerated Loop

```swift
for (index, number) in numbers.enumerated() {
    print("Index \(index): \(number)")
}
```

#### stride
Returns a sequence from a starting value to, but not including, an end value, stepping by the specified amount.
``` swift
for countdown in stride(from: 3, to: 0, by: -1) {
    print("\(countdown)...")
}
// 3...
// 2...
// 1...
```



### Array Properties and Methods

#### Count and isEmpty

```swift
print(numbers.count)     // Number of elements
print(numbers.isEmpty)   // true if empty, false otherwise; use with guard some times
```

#### Contains

```swift
if numbers.contains(3) { // will be O(n) time complexity, think about using set
    print("Array contains 3")
}
```

#### First and Last

```swift
if let first = numbers.first, let last = numbers.last {
    print("First: \(first), Last: \(last)")
}
```

### Slicing Arrays

```swift
let slice = numbers[1...3] // Creates an ArraySlice
let subArray = Array(slice) // Converts to Array if needed
```

#### Prefix and Suffix

```swift
let numbers = [1, 2, 3, 4, 5]
let prefix = numbers.prefix(2) // [1, 2]
let suffix = numbers.suffix(2) // [4, 5]
```

#### Drop First and Last

```swift
var numbers = [1, 2, 3, 4, 5]
numbers.dropFirst() // [2, 3, 4, 5]
numbers.dropLast() // [1, 2, 3, 4]
```

### Combining Arrays

#### Concatenation

```swift
let combinedArray = numbers + [5, 6, 7]
```

#### Append Contents Of

```swift
numbers.append(contentsOf: [8, 9])
```

### Sorting Arrays


```swift
//Default Sort
let sortedNumbers = numbers.sorted()
// In-Place Sort
numbers.sort()

```

#### Custom Sort

```swift
let customSorted = numbers.sorted { $0 > $1 } // Sort in descending order

// Sorting an array of custom objects
struct Person {
    var name: String
    var age: Int
}
let people = [Person(name: "Alice", age: 30), Person(name: "Bob", age: 25)]
let sortedPeople = people.sorted(by: \.age) // Sort by age
```

### Shuffle Array

```swift
let shuffledNumbers = numbers.shuffled()
```

### Functional Programming with Arrays

#### Map

Transforms each element.

```swift
let squaredNumbers = numbers.map { $0 * $0 }
```

#### Filter

Filters elements based on a condition.

```swift
let evenNumbers = numbers.filter { $0 % 2 == 0 }
```

#### Reduce

Combines elements into a single value.

```swift
let sum = numbers.reduce(0, +)
```

### Multi-Dimensional Arrays

```swift
var matrix: [[Int]] = [
    [1, 2],
    [3, 4],
    [5, 6]
]

// Accessing elements
let element = matrix[0][1] // 2
```

### Copying Arrays

Arrays are value types in Swift not reference types. When you assign an array to another variable, a copy is made.

```swift
var original = [1, 2, 3]
var copy = original
copy.append(4)

// original: [1, 2, 3]
// copy: [1, 2, 3, 4]
```

### Common Array Operations

#### Finding an Element's Index

```swift
if let index = numbers.firstIndex(of: 10) {
    print("Index of 10 is \(index)")
}
```

#### Removing Duplicates

```swift
let uniqueNumbers = Array(Set(numbers))
```

> **Note:** Converting to a `Set` removes duplicates but may change the order.

#### Reversing an Array

```swift
let reversedNumbers = numbers.reversed()
```

#### Checking Equality

```swift
let arrayA = [1, 2, 3]
let arrayB = [1, 2, 3]
print(arrayA == arrayB) // true
```

### String to Array 
Strings in Swift can be difficult to work with because you can not index into them like you can with arrays. However, you can convert a string to an array of characters and then work with it like an array.

```swift
let str = "Hello, World!"
let charArray = Array(str)
print(charArray[3]) // l
```



## Sets in Swift

Sets are unordered collections of unique elements. They are commonly used when the order of elements is not important but uniqueness is essential. Sets are beneficial for operations like membership checking, removing duplicates, and performing mathematical set operations.

### Creating Sets

#### Empty Set

```swift
var emptySet: Set<Int> = []
// Or using the Set initializer
var anotherEmptySet: Set<Int> = Set()
```

#### Set with Initial Values

```swift
let numbers: Set = [1, 2, 3, 4, 5]

// or from an array
let numberArray = [1, 2, 3, 4, 5]
let numberSet = Set(numberArray)

```

### Accessing Elements

#### Check if Set is Empty

```swift
if numbers.isEmpty {
    print("The set is empty.")
}
```

#### Count of Elements

```swift
print("The set has \(numbers.count) elements.")
```

### Modifying Sets

#### Adding Elements

```swift
var mutableSet: Set<Int> = [1, 2, 3]
mutableSet.insert(4) // Adds 4 to the set
```

#### Removing Elements

```swift
mutableSet.remove(2) // Removes 2 from the set
```

#### Removing All Elements

```swift
mutableSet.removeAll() // Clears the set
```

### Set Properties and Methods

#### Check for Containment
Done in O(1) time complexity which is why these are so useful

```swift
if mutableSet.contains(1) {
    print("The set contains 1.")
}
```

#### Iterating Over a Set

```swift
for number in numbers {
    print(number)
}
```

### Common Operations

#### Union of Sets

```swift
let setA: Set = [1, 2, 3]
let setB: Set = [3, 4, 5]
let unionSet = setA.union(setB) // [1, 2, 3, 4, 5]
```

#### Intersection of Sets

```swift
let intersectionSet = setA.intersection(setB) // [3]
```

#### Difference of Sets

```swift
let differenceSet = setA.subtracting(setB) // [1, 2]
```

#### Symmetric Difference

```swift
let symmetricDifferenceSet = setA.symmetricDifference(setB) // [1, 2, 4, 5]
```


### Set Membership and Comparison

#### Membership Check

```swift
if setA.contains(1) {
    print("1 is in setA.")
}
```

#### Comparing Sets

```swift
let isSubset = setA.isSubset(of: unionSet) // true, meaning setA is contained in unionSet
let isSuperset = unionSet.isSuperset(of: setA) // true, meaning unionSet contains all elements of setA
let isDisjoint = setA.isDisjoint(with: setB) // false, meaning they have elements in common
```

### Using Sets with Custom Types

To use custom types with Sets, the type must conform to the `Hashable` protocol.

```swift
struct Person: Hashable {
    var name: String
    var age: Int
}

let people: Set<Person> = [Person(name: "Alice", age: 30), Person(name: "Bob", age: 25)]
```

### direct-access-array-as-a-set
Some times there is a set number of elements that you know will be in the set. In this case, you can use an array as a set. This is useful because you can access elements in O(1) time complexity. Useful for examples where you are counting the number of times a character appears in a string.

```swift
let alphabet = Array(repeating: 0, count: 26)
let aAscii = Character("a").asciiValue!
for c in "hello" {
    let index = Int(c.asciiValue! - aAscii)
    alphabet[index] += 1
}
print(alphabet[7]) // 1
```



## Dictionaries in Swift

Dictionaries are collections of key-value pairs, where each key is unique. They are often used for lookups, mappings, and storing data associated with specific keys.

### Creating Dictionaries

#### Empty Dictionary

```swift
var emptyDict: [String: Int] = [:]
// Or using the Dictionary initializer
var anotherEmptyDict = Dictionary<String, Int>()
```

#### Dictionary with Initial Values

```swift
let ages: [String: Int] = ["Alice": 30, "Bob": 25, "Charlie": 35]
```

### Accessing Elements

#### Retrieving Values

```swift
let aliceAge = ages["Alice"] // Optional(30)
```

#### Safe Access

```swift
if let age = ages["Bob"] {
    print("Bob's age is \(age).")
} else {
    print("Bob is not found in the dictionary.")
}
```

#### Default Value

```swift
// lots of times you will want to have a non optional value of 0 or the value 
let unknownAge = ages["David", default: 40] // 40
```

### Modifying Dictionaries

#### Adding Key-Value Pairs

```swift
var mutableAges = ages
mutableAges["David"] = 40 // Adds David with age 40
```

#### Updating Values

```swift
mutableAges["Alice"] = 31 // Updates Alice's age to 31
```

#### Removing Key-Value Pairs

```swift
mutableAges.removeValue(forKey: "Charlie") // Removes Charlie from the dictionary
```

#### Removing All Elements

```swift
mutableAges.removeAll() // Clears the dictionary
```

### Dictionary Properties and Methods

#### Count of Key-Value Pairs

```swift
print("The dictionary has \(ages.count) entries.")
```

#### Check if Dictionary is Empty

```swift
if ages.isEmpty {
    print("The dictionary is empty.")
}
```

#### Iterating Over a Dictionary

```swift
// key, value
for (name, age) in ages {
    print("\(name) is \(age) years old.")
}
```

### Common Operations

#### Checking for Key Existence

```swift
if ages.keys.contains("Alice") {
    print("Alice is in the dictionary.")
}
```

#### Getting All Keys and Values

```swift
let keys = Array(ages.keys)   // ["Alice", "Bob", "Charlie"]
let values = Array(ages.values) // [30, 25, 35]
```

### Merging Dictionaries

#### Merging Two Dictionaries

```swift
let additionalAges: [String: Int] = ["Eve": 22, "Frank": 28]
let mergedAges = ages.merging(additionalAges) { (current, _) in current }
// Merged dictionary will keep the existing values
```

### Using Dictionaries with Custom Types

To use custom types as keys, the type must conform to the `Hashable` protocol.

```swift
struct Person: Hashable {
    var name: String
    var age: Int
}

let peopleDict: [Person: String] = [
    Person(name: "Alice", age: 30): "Engineer",
    Person(name: "Bob", age: 25): "Designer"
]
```

## Stacks in Swift
Stacks in swift can be represented using arrays. Stacks are a Last In First Out (LIFO) data structure, where elements are added and removed from the same end. Stacks are used in many algorithms and can be implemented using arrays or linked lists.
### Creating a Stack

```swift
var stack: [Int] = [] // Create an empty stack
```

### Push and Pop Operations

#### Pushing Elements

```swift
stack.append(1) // Stack is now [1]
stack.append(2) // Stack is now [1, 2]
stack.append(3) // Stack is now [1, 2, 3]
```

#### Popping Elements

```swift
let poppedElement = stack.popLast() // Removes and returns 3
```

### Peek Operation
```swift
if let topElement = stack.last {
    print("The top element is \(topElement).")
} else {
    print("The stack is empty.")
}
```

## Queues in Swift
Queues in swift can be represented using arrays (will not get dequeue in O(1)). Queues are a First In First Out (FIFO) data structure, where elements are added at the back and removed from the front. Queues are used in many algorithms and can be implemented using arrays or linked lists.

### Creating a Queue

```swift
var queue: [Int] = [] // Create an empty queue
```

### Enqueue and Dequeue Operations

#### Enqueue Elements

```swift
queue.append(1) // Queue is now [1]
queue.append(2) // Queue is now [1, 2]
queue.append(3) // Queue is now [1, 2, 3]
```

#### Dequeue Elements

```swift
let dequeuedElement = queue.removeFirst() // Removes and returns 1
```

### Peek Operation
```swift
if let frontElement = queue.first {
    print("The front element is \(frontElement).")
} else {
    print("The queue is empty.")
}
```

## Heap/Priority Queue in Swift
A Heap (or Priority Queue) is a tree-based data structure that ensures the element with the highest (or lowest) priority is always at the root. A heap can either be a min-heap (where the smallest element is at the root) or a max-heap (where the largest element is at the root). Heaps are often used for implementing priority queues and are useful in algorithms like Dijkstra’s shortest path, Huffman coding, and more. I will use the heap from Collections \

### Creating a Heap

```swift
import Collections

var heap = Heap<Int>

```

### Inserting Elements

```swift
heap.insert(3)
heap.insert(2)
heap.insert(1)
```

### Min and Max Lookup
This is done in constant time 
```swift
let minElement = heap.min() // 1
let maxElement = heap.max() // 3
```

### Removing Elements
Removal has logarithmic complexity, and removing both the smallest and largest elements is supported
```swift
let minElement = heap.popMin() // 1
let maxElement = heap.popMax() // 3
```
