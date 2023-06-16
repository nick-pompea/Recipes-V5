
# Gestures

 [Long Press Gesture](basics/Gesture.md)
---

## Magnification
* Modifier
```swift
            Rectangle()
                .scaleEffect(1 + currentAmount)
//
                .gesture(
                    MagnificationGesture()
                        .onChanged {value in
                            currentAmount = value - 1
                            
                        }
                        .onEnded {value in
                            withAnimation(.spring()) {
                                currentAmount = 0
                            }
                        }
                )
```
[Youtube Tutorial](https://www.youtube.com/watch?v=RkfJoNzfJ8w&t=0s)

