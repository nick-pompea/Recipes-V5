# @escaping

Example
```swift
    func downloadDataThree(CompletionHandler: @escaping (_ data: String) -> Void) {
        DispatchQueue.main.asyncAfter(deadline: .now() + 2.0){
            CompletionHandler("New data")
        }
    }
```
[Youtube Tutorial](https://www.youtube.com/watch?v=7gg8iBH2fg4&t=0s)
