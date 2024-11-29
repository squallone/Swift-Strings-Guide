<img src="https://github.com/user-attachments/assets/91d03879-0917-4c5c-943c-2d9d102afd41" width=80%>

This guide covers various APIs of `String` in Swift, along with examples and expected outputs. Each API is categorized for clarity. 

## Table of Contents
1. [Introduction to Strings in Swift](#introduction-to-strings-in-swift)
2. [Basic String Initialization](#basic-string-initialization)
3. [String Properties](#string-properties)
4. [String Manipulation](#string-manipulation)
    - [Concatenation](#concatenation)
    - [Interpolation](#interpolation)
    - [Modification](#modification)
5. [String Searching](#string-searching)
    - [Finding Substrings](#finding-substrings)
    - [Contains](#contains)
    - [Prefix and Suffix](#prefix-and-suffix)
6. [String Splitting and Joining](#string-splitting-and-joining)
    - [Splitting Strings](#splitting-strings)
    - [Joining Strings](#joining-strings)
7. [String Iteration](#string-iteration)
8. [String Comparison](#string-comparison)
    - [Equality and Comparison](#equality-and-comparison)
    - [Case Insensitive Comparison](#case-insensitive-comparison)
9. [String Encoding and Decoding](#string-encoding-and-decoding)
10. [String Transformations](#string-transformations)
    - [Uppercase and Lowercase](#uppercase-and-lowercase)
    - [Trimming Whitespaces](#trimming-whitespaces)
11. [Substring Handling](#substring-handling)
12. [Advanced String Operations](#advanced-string-operations)
    - [Regular Expressions](#regular-expressions)
    - [Unicode and Character Sets](#unicode-and-character-sets)
13. [String Performance Tips](#string-performance-tips)
14. [Conclusion](#conclusion)

---

## 1. Introduction to Strings in Swift
A `String` in Swift represents a series of characters in a specific order. Swift strings are Unicode-compliant, ensuring support for a wide range of characters and languages.

```swift
let greeting = "Hello, World!"
print(greeting) // Output: Hello, World!
```

---

## 2. Basic String Initialization
### Example
```swift
let emptyString = ""
let predefinedString = "Swift"
print(emptyString.isEmpty)  // Output: true
print(predefinedString)     // Output: Swift
```

---

## 3. String Properties
### Example
```swift
let sample = "Hello, Swift!"

print(sample.count)          // Output: 13
print(sample.isEmpty)        // Output: false
print(sample.first)          // Output: Optional("H")
print(sample.last)           // Output: Optional("!")
```

---

## 4. String Manipulation

### Concatenation
```swift
let part1 = "Hello"
let part2 = "World"
let full = part1 + ", " + part2 + "!"
print(full) // Output: Hello, World!
```

### Interpolation
```swift
let name = "John"
let greeting = "Hello, \(name)!"
print(greeting) // Output: Hello, John!
```

### Modification
```swift
var mutableString = "Swift"
mutableString += " Programming"
print(mutableString) // Output: Swift Programming
```

---

## 5. String Searching

### Finding Substrings
```swift
let text = "Hello, Swift!"
if let range = text.range(of: "Swift") {
    print("Found at range: \(range)")
}
// Output: Found at range: Range
```

### Contains
```swift
let result = text.contains("Swift")
print(result) // Output: true
```

### Prefix and Suffix
```swift
let isPrefix = text.hasPrefix("Hello")
let isSuffix = text.hasSuffix("!")
print(isPrefix) // Output: true
print(isSuffix) // Output: true
```

---

## 6. String Splitting and Joining

### Splitting Strings
```swift
let sentence = "Swift is fun"
let words = sentence.split(separator: " ")
print(words) // Output: ["Swift", "is", "fun"]
```

### Joining Strings
```swift
let array = ["Swift", "is", "fun"]
let joined = array.joined(separator: " ")
print(joined) // Output: Swift is fun
```

---

## 7. String Iteration
```swift
for character in "Swift" {
    print(character)
}
// Output: S w i f t
```

---

## 8. String Comparison

### Equality and Comparison
```swift
let string1 = "Swift"
let string2 = "Swift"
print(string1 == string2) // Output: true
```

### Case Insensitive Comparison
```swift
let equal = string1.caseInsensitiveCompare("swift") == .orderedSame
print(equal) // Output: true
```

---

## 9. String Encoding and Decoding
```swift
let utf8Data = "Hello".data(using: .utf8)!
print(utf8Data) // Output: UTF8 data
```

---

## 10. String Transformations

### Uppercase and Lowercase
```swift
let text = "Swift"
print(text.uppercased()) // Output: SWIFT
print(text.lowercased()) // Output: swift
```

### Trimming Whitespaces
```swift
let spaced = "  Hello  "
print(spaced.trimmingCharacters(in: .whitespaces)) // Output: Hello
```

---

## 11. Substring Handling
```swift
let text = "Hello, Swift!"
let start = text.startIndex
let end = text.index(text.startIndex, offsetBy: 5)
let substring = text[start..<end]
print(substring) // Output: Hello
```

---

## 12. Advanced String Operations

### Regular Expressions
```swift
import Foundation

let regex = try! NSRegularExpression(pattern: "[a-zA-Z]+")
let matches = regex.matches(in: "Swift 2024", range: NSRange("Swift 2024".startIndex..., in: "Swift 2024"))
print(matches.count) // Output: 1
```

### Unicode and Character Sets
```swift
let unicode = "Swift 🚀"
print(unicode.unicodeScalars) // Output: Unicode scalars of "Swift 🚀"
```

---

## 13. String Performance Tips
- Use `Substring` when working with slices for better performance.
- Avoid repeated string concatenation; use `StringBuilder`-like methods (e.g., `append`).
