# Strings in Swift

In Swift, strings are represented by the `String` type, which offers a wide variety of APIs to manipulate and query string values. These APIs cover everything from simple string operations to advanced Unicode handling. Below is a detailed overview of the available APIs for strings in Swift, along with examples and expected outputs.

### Basic String Initialization

#### `String` Initialization
- **`String()`**: Initializes an empty string.
- **`String(repeating:count:)`**: Initializes a string with a repeated character or substring.

```swift
let emptyString = String()
print(emptyString)  // Output: ""

let repeatedString = String(repeating: "A", count: 5)
print(repeatedString)  // Output: "AAAAA"
```
---

### **String Concatenation**

#### `+` (String Addition)
- **`+`**: Concatenates two strings.

```swift
let first = "Hello"
let second = "World"
let greeting = first + " " + second
print(greeting)  // Output: "Hello World"
```

#### `+=` (Append Assignment)
- **`+=`**: Appends a string to an existing string.

```swift
var message = "Hello"
message += " Swift"
print(message)  // Output: "Hello Swift"
```

---

### **String Length**

#### `count`
- **`count`**: Returns the number of characters in the string.

```swift
let phrase = "Hello, World!"
print(phrase.count)  // Output: 13
```

---

### **String Comparison**

#### `==` (Equality Operator)
- **`==`**: Checks if two strings are equal.

```swift
let str1 = "apple"
let str2 = "apple"
let str3 = "orange"
print(str1 == str2)  // Output: true
print(str1 == str3)  // Output: false
```

#### `!=` (Inequality Operator)
- **`!=`**: Checks if two strings are not equal.

```swift
print(str1 != str3)  // Output: true
```

#### `compare(_:)`
- **`compare(_:)`**: Compares two strings lexicographically.

```swift
let result = str1.compare(str2)
switch result {
case .orderedAscending:
    print("\(str1) is less than \(str2)")
case .orderedDescending:
    print("\(str1) is greater than \(str2)")
case .orderedSame:
    print("\(str1) is equal to \(str2)")
}
// Output: "apple is equal to apple"
```

---

### **String Substring**

#### `prefix(_:)` and `suffix(_:)`
- **`prefix(_:)`**: Returns the initial part of the string up to the given number of characters.
- **`suffix(_:)`**: Returns the final part of the string starting from the given number of characters.

```swift
let text = "Hello, World!"
print(text.prefix(5))  // Output: "Hello"
print(text.suffix(6))  // Output: "World!"
```

#### `subscript` for Range Access
- **`subscript(range:)`**: Extracts a substring from a string using a range.

```swift
let substring = text[text.index(text.startIndex, offsetBy: 0)..<text.index(text.startIndex, offsetBy: 5)]
print(substring)  // Output: "Hello"
```

---

### **String Case Conversion**

#### `lowercased()` and `uppercased()`
- **`lowercased()`**: Converts the string to lowercase.
- **`uppercased()`**: Converts the string to uppercase.

```swift
let mixedCase = "HeLLo WoRLd"
print(mixedCase.lowercased())  // Output: "hello world"
print(mixedCase.uppercased())  // Output: "HELLO WORLD"
```

#### `capitalized`
- **`capitalized`**: Capitalizes the first letter of each word.

```swift
let title = "the swift programming language"
print(title.capitalized)  // Output: "The Swift Programming Language"
```

---

### **String Trimming**

#### `trimmingCharacters(in:)`
- **`trimmingCharacters(in:)`**: Removes characters from the start and end of the string based on a given character set.

```swift
let paddedString = "  Hello, World!  "
print(paddedString.trimmingCharacters(in: .whitespaces))  // Output: "Hello, World!"
```

---

### **String Search**

#### `contains(_:)`
- **`contains(_:)`**: Checks if a substring exists within the string.

```swift
let sentence = "The quick brown fox jumps over the lazy dog"
print(sentence.contains("quick"))  // Output: true
print(sentence.contains("cat"))    // Output: false
```

#### `range(of:)`
- **`range(of:)`**: Returns the range of the first occurrence of a substring.

```swift
let searchString = "apple pie"
if let range = searchString.range(of: "pie") {
    print("Found at index: \(searchString.distance(from: searchString.startIndex, to: range.lowerBound))")
    // Output: "Found at index: 6"
}
```

#### `firstIndex(of:)` and `lastIndex(of:)`
- **`firstIndex(of:)`**: Finds the first occurrence of a character.
- **`lastIndex(of:)`**: Finds the last occurrence of a character.

```swift
let word = "banana"
print(word.firstIndex(of: "a"))  // Output: Optional(3)
print(word.lastIndex(of: "a"))   // Output: Optional(5)
```

---

### **String Replacement**

#### `replacingOccurrences(of:with:)`
- **`replacingOccurrences(of:with:)`**: Replaces occurrences of a substring with another string.

```swift
let message = "Hello, World!"
let updatedMessage = message.replacingOccurrences(of: "World", with: "Swift")
print(updatedMessage)  // Output: "Hello, Swift!"
```

#### `replacingCharacters(in:with:)`
- **`replacingCharacters(in:with:)`**: Replaces a substring in the specified range with a new string.

```swift
let replaceString = "Hello, World!"
var mutableString = replaceString
mutableString.replaceSubrange(mutableString.range(of: "World")!, with: "Swift")
print(mutableString)  // Output: "Hello, Swift!"
```

---

### **String Encoding and Decoding**

#### `data(using:)`
- **`data(using:)`**: Converts a string to `Data` using the specified encoding.

```swift
let text = "Hello, Swift!"
if let data = text.data(using: .utf8) {
    print(data)  // Output: 11 bytes of data representation
}
```

#### `String(data:encoding:)`
- **`init(data:encoding:)`**: Converts `Data` back into a string.

```swift
let data = "Hello, Swift!".data(using: .utf8)!
let decodedString = String(data: data, encoding: .utf8)!
print(decodedString)  // Output: "Hello, Swift!"
```

---

### **String Unicode Handling**

#### `unicodeScalars`
- **`unicodeScalars`**: Returns the Unicode scalar values of the string.

```swift
let hello = "Hello"
for scalar in hello.unicodeScalars {
    print(scalar)
}
// Output: U+0048 (H)
//         U+0065 (e)
//         U+006C (l)
//         U+006C (l)
//         U+006F (o)
```

#### `characters`
- **`characters`**: Returns the string's characters as a sequence.

```swift
let word = "Swift"
for character in word {
    print(character)
}
// Output: 
// S
// w
// i
// f
// t
```

---

### **String Split**

#### `split(separator:)`
- **`split(separator:)`**: Splits a string into an array of substrings based on a separator.

```swift
let sentence = "apple,banana,orange"
let fruits = sentence.split(separator: ",")
print(fruits)  // Output: ["apple", "banana", "orange"]
```

---

### **String Validation**

#### `isEmpty`
- **`isEmpty`**: Checks if the string is empty.

```swift
let emptyString = ""
let nonEmptyString = "Hello"
print(emptyString.isEmpty)  // Output: true
print(nonEmptyString.isEmpty)  // Output: false
```

#### `hasPrefix(_:)` and `hasSuffix(_:)`
- **`hasPrefix(_:)`**: Checks if the string starts with the given prefix.
- **`hasSuffix(_:)`**: Checks if the string ends with the given suffix.

```swift
let url = "https://www.example.com"
print(url.hasPrefix("https"))  // Output: true
print(url.hasSuffix(".com"))   // Output: true
```
