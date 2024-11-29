<img src="https://github.com/user-attachments/assets/91d03879-0917-4c5c-943c-2d9d102afd41" width=80%>

This guide covers various APIs of `String` in Swift, along with examples and expected outputs. Each API is categorized for clarity. 

## Table of Contents
1. [Introduction to Strings in Swift](#1-introduction-to-strings-in-swift)
2. [Basic String Initialization](#2-basic-string-initialization)
3. [String Properties](#3-string-properties)
4. [String Manipulation](#4-string-manipulation)
    - [Concatenation](#concatenation)
    - [Interpolation](#interpolation)
    - [Modification](#modification)
5. [String Searching](#5-string-searching)
    - [Finding Substrings](#finding-substrings)
    - [Contains](#contains)
    - [Prefix and Suffix](#prefix-and-suffix)
6. [String Splitting and Joining](#6-string-splitting-and-joining)
    - [Splitting Strings](#splitting-strings)
    - [Joining Strings](#joining-strings)
7. [String Iteration](#7-string-iteration)
8. [String Comparison](#8-string-comparison)
    - [Equality and Comparison](#equality-and-comparison)
    - [Case Insensitive Comparison](#case-insensitive-comparison)
9. [String Encoding and Decoding](#9-string-encoding-and-decoding)
10. [String Transformations](#10-string-transformations)
    - [Uppercase and Lowercase](#uppercase-and-lowercase)
    - [Trimming Whitespaces](#trimming-whitespaces)
11. [Substring Handling](#11-substring-handling)
12. [Advanced String Operations](#12-advanced-string-operations)
    - [Regular Expressions](#regular-expressions)
    - [Unicode and Character Sets](#unicode-and-character-sets)
13. [String Performance Tips](#13-string-performance-tips)

---

## 1. Introduction to Strings in Swift
A `String` in Swift represents a series of characters in a specific order. Swift strings are Unicode-compliant, ensuring support for a wide range of characters and languages.

```swift
let greeting = "Hello, World!"
print(greeting) // Output: Hello, World!
```

## 2. Basic String Initialization
### Example
```swift
let emptyString = ""
let predefinedString = "Swift"
print(emptyString.isEmpty)  // Output: true
print(predefinedString)     // Output: Swift
```

## 3. String Properties
### Example
```swift
let sample = "Hello, Swift!"

print(sample.count)          // Output: 13
print(sample.isEmpty)        // Output: false
print(sample.first)          // Output: Optional("H")
print(sample.last)           // Output: Optional("!")
```

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

### Drop & Remove

#### **`dropFirst` and `dropLast`**
- Create a new `Substring` by removing the first or last character(s) from the string.  
- These methods do not modify the original string. Instead, they return a `Substring`.

```swift
var name = "Tom Dick Harry"

print(name.dropFirst())      // "om Dick Harry" (removes the first character)
print(name.dropLast())       // "Tom Dick Harr" (removes the last character)
print(name.dropFirst(3))     // " Dick Harry" (removes the first 3 characters)
print(name.dropLast(5))      // "Tom Dick " (removes the last 5 characters)

// Original string remains unchanged
print(name)                  // "Tom Dick Harry"
```

#### **`removeFirst` and `removeLast`**
- Remove the first or last character(s) directly from the original string.  
- These methods modify the original string in place.

```swift
var name = "Tom Dick Harry"

// Remove a single character
name.removeFirst()           // Removes "T"
print(name)                  // "om Dick Harry"

// Remove the last character
name.removeLast()            // Removes "y"
print(name)                  // "om Dick Harr"

// Remove a specific number of characters
name.removeFirst(3)          // Removes "om "
print(name)                  // "Dick Harr"

name.removeLast(5)           // Removes " Harr"
print(name)                  // "Dick"
```

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

## 7. String Iteration
```swift
for character in "Swift" {
    print(character)
}
// Output: S w i f t
```

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

## 9. String Encoding and Decoding
```swift
let utf8Data = "Hello".data(using: .utf8)!
print(utf8Data) // Output: UTF8 data
```

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

## 11. Substring Handling
```swift
let text = "Hello, Swift!"
let start = text.startIndex
let end = text.index(text.startIndex, offsetBy: 5)
let substring = text[start..<end]
print(substring) // Output: Hello
```

### **String vs Substring**

| Feature            | String                     | Substring                      |
|--------------------|----------------------------|---------------------------------|
| **Ownership**      | Owns its memory           | Shares memory with the original string |
| **Performance**    | Better for long-term storage and manipulation | More efficient for temporary operations |
| **Use Case**       | General-purpose text storage | Temporary slices of strings   |
| **Conversion**     | Not needed                | Must convert to `String` for independent use |
| **Memory**         | Allocates new memory     | Avoids memory allocation by referencing original `String` |

```swift
let fullString: String = "Hello, Swift"
let substring: Substring = fullString.prefix(5) // "Hello"
let newString: String = String(substring) // Now independent
```

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

## 13. String Performance Tips
- Use `Substring` when working with slices for better performance.
- Avoid repeated string concatenation; use `StringBuilder`-like methods (e.g., `append`).
