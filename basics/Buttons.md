
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
