# Control Flow

if 
```swift
@State var isLoading: Bool = false

if isLoading {
ProgressView()
}
```

if else
```swift
@State var isLoading: Bool = false

if isLoading {
ProgressView()
} else {
MainView()
}
```
[Youtube Tutorial](https://www.youtube.com/watch?v=W8sGT16WAkQ&t=0s)


Ternary Operator
```swift
Color(isLoading ? Color.black : Color.red)
```
[Youtube Tutorial](https://www.youtube.com/watch?v=xzFSOdpxy-o&t=0s)

Guard
* https://www.programiz.com/swift-programming/guard-statement
```swift
guard expression else {
  // statements
  // control statement: return, break, continue or throw.
}
```



Switch
