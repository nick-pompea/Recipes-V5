
# Colors

Dark / Light Mode

Examples

```swift
        NavigationView(){
            ScrollView{
                VStack(spacing: 20){
                    Text("Primary")
                        .foregroundColor(.primary)
                    Text("Secondary")
                        .foregroundColor(.secondary)
                    Text("Black")
                        .foregroundColor(.black)
                    Text("White")
                        .foregroundColor(.white)
                    Text("Red")
                        .foregroundColor(.red)
                    Text("Global Adaptive")
                        .foregroundColor(Color("adaptiveColor"))
                    Text("Local Adaptive")
                        .foregroundColor(colorScheme == .light ? .green : .yellow)
                }
            }
            .navigationTitle("Dark Mode Colors")
        }
```

Check if light or dark mode

```swift
    @Environment(\.colorScheme) var colorScheme
```

[Youtube Tutorial](https://www.youtube.com/watch?v=DB5uNhIea-o&t=0s)


---

* [Gradients](basics/Gradients.md)



