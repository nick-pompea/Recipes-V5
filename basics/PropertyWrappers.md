
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


---


## Environment Object 
 
* Allows access of an item from all parts of a project. 
* Placed in @ Main and refrecned as needed in each view or class
* Commonly a class

Setup
* 1 - Make Class
```swift
class Model: ObservableObject {
}
```
* 2 - Place reference in @ main
```swift
@main
struct Recepies_v2App: App {
    
   @StateObject var Model: Model = Model()
    
    var body: some Scene {
        WindowGroup {
            ContentView()
           .environmentObject(Model)
        }
    }
}
```
* 3 - Pull from environment as needed
```swift
    @StateObject var viewModel: Model = Model()
```
* 4 - Update preview ( Or else XCode will crash) 
```swift
    struct EnvironmentObjectView_Previews: PreviewProvider {
    static var previews: some View {
       View()
         .environmentObject(Model())
    }
}
```

