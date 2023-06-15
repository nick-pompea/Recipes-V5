
# Property Wrappers ( Decorations ) 


@State

```swift
      @State var tapCount = 0
    var body: some View {
        Button("Tap Count: \(tapCount)") {
        tapCount += 1
    }
}
}

```
[Youtube Tutorial](https://www.youtube.com/watch?v=aNYuDi8C29E)


@Binding
Child View
```swift
@Binding var backgroundColor: Color
```
Parent View
```swift
@State var mainVar: Color = Color.green

ChildView(backgroundColor: $mainVar)
```
[Youtube Tutorial](https://www.youtube.com/watch?v=btDMzB5x2Gs&t=0s)


