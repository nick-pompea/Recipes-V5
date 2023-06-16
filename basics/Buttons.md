
# Buttons

Default 
```swift
 Button {
Save()
} label: {
Text("Save")
}
```
Modifiers 
```swift
.buttonStyle(.borderedProminent)
```

[Youtube Tutorial](https://youtu.be/kTARSJSNGPI)


## Context Menu

Modifiers
```swift
        .contextMenu {
            Button {
                backgroundColor = .yellow
            } label: {
                Label("Share", systemImage: "flame.fill" )
            }
            
            Button {
                backgroundColor = .red
            } label: {
                Label("Save", systemImage: "folder.fill" )
            }
            
            Button {
                backgroundColor = .green
            } label: {
                HStack{
                    Text("Like")
                    Image(systemName: "heart.fill")
                }
            }
        }
```

[Youtube Tutorial](https://www.youtube.com/watch?v=3jjQ6WASGIw&t=0s)

---

## Long Press Gesture

```swift
                   .onLongPressGesture(minimumDuration: 1, maximumDistance: 50) { (isPressing) in
                        //start of press to min duration
                        if isPressing {
                            withAnimation(.easeOut(duration: 1.0) ) {
                                isCompleted = true
                            }
                        } else {
                            DispatchQueue.main.asyncAfter(deadline: .now() + 0.1) {
                                if !isSucess {
                                    withAnimation(.easeInOut) {
                                        isCompleted = false
                                    }
                                }
                            }
                        }


```
[Youtube Tutorial](https://www.youtube.com/watch?v=Ioux-yqewNs&t=0s)

