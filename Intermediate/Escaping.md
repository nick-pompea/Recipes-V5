# @escaping


* Function 

```

func example(completionHandler: @escaping (_ item1: String, _ item2: String) -> ()) {

}
```

* Inside Function

```
completionHandler(    ,     )
```


* Calling

```
example { item1, item2 in

}
```
----



Example
```swift
    func downloadDataThree(CompletionHandler: @escaping (_ data: String) -> Void) {
        DispatchQueue.main.asyncAfter(deadline: .now() + 2.0){
            CompletionHandler("New data")
        }
    }
```
[Youtube Tutorial](https://www.youtube.com/watch?v=7gg8iBH2fg4&t=0s)
