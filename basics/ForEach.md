# For Each

Values
```swift
let data: [String] = ["One", "Two", "Three"]

ForEach(data.indices) { i in
Text("New Itesm: \(data[i])")
}

```

Series
```swift
ForEach(0..<10) {index in
HStack {
Circle()
.frame(width: 30, height: 30)
Text("\(index)")
}
}

```
[Youtube Tutorial](https://www.youtube.com/watch?v=CKmsqRN-VM0&list=RDCMUCp25X4LzOLaksp5qY0YMUzg&index=2)


