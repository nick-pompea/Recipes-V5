# Init

Basic
```swift
  let backGroundColor: Color
    let count: Int
    let title: String
    
    init(backGroundColor: Color, count: Int, title: String) {
        self.backGroundColor = backGroundColor
        self.count = count
        self.title = title
    }
```

With control flow
```swift
  let backGroundColor: Color
    let count: Int
    let title: String
    
    init(backGroundColor: Color, count: Int, title: String) {
        self.backGroundColor = backGroundColor
        self.count = count
        self.title = title
        
                if fruit == .apple {
            self.title = "Apples"
            self.backGroundColor = Color.red
        } else {
            self.title = "Oranges"
            self.backGroundColor = Color.orange
        }
    }
```
[Youtube Tutorial](https://www.youtube.com/watch?v=su0KLQq0JM0&t=518s)
