
# Tap Gesture

Single Tap
```swift
.onTapGesture {
isSelected.toggle()
}
                    
                    
.onTapGesture(count: 1, perform: {
isSelected.toggle()
})
         
```


Double Tap
```swift
.onTapGesture(count: 2, perform: {
isSelected.toggle()
})
```
