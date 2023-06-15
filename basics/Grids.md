
# Grids

GridItems
```swift
GridItem(.flexible())
GridItem(.fixed(75))
GridItem(.adaptive(minimum: 150, maximum: 300))
```

Can be used in an array

flexible
```swift
    let columns: [GridItem] = [
        GridItem(.flexible(), spacing: nil, alignment: nil),
        GridItem(.flexible(), spacing: nil, alignment: nil),
        GridItem(.flexible(), spacing: nil, alignment: nil)
]
```

adaptive
```swift
    let columns: [GridItem] = [
            GridItem(.adaptive(minimum: 150, maximum: 300 ), spacing: nil, alignment: nil)),
            GridItem(.adaptive(minimum: 150, maximum: 300 ), spacing: nil, alignment: nil)),
]
```
fixed
```swift
    let columns: [GridItem] = [
            GridItem(.fixed(75), spacing: nil, alignment: nil),
            GridItem(.fixed(100), spacing: nil, alignment: nil),
            GridItem(.fixed(75), spacing: nil, alignment: nil),
            GridItem(.fixed(50), spacing: nil, alignment: nil)
]
```



[Youtube Tutorial](https://www.youtube.com/watch?v=vHvb7LH8VuE&t=0s)

