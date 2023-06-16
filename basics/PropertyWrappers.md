
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

@Published
* Like @State but for classes
```swift
    @Published var isLoading: Bool = false

```
---

## ObservableObject

* For class so other code can acces
```swift
class FruitViewModel: ObservableObject {
}
```

[Youtube Tutorial](https://www.youtube.com/watch?v=-yjKAb0Pj60&t=0s)

---

Identifiable

* Add to items that need an ID 
* Commonly used to iterate through with a struct used in a for each loop
```swift
struct fuitModel: Identifiable {
}
```

Can add an automatic ID with UUID() or UUID().uuidString
```swift
struct fuitModel: Identifiable {
    let id: String = UUID().uuidString
```
