# Sheets

* Can only use on for each view 

Modifiers
```swift
.sheet(isPresented: $showSheet) {
secondScreen()
}
```

# FullScreenCover

Modifiers
```swift
.fullScreenCover(isPresented: $showSheet) {
secondScreen()
}
```
[Youtube Tutorial](https://www.youtube.com/watch?v=ddr3E0l4gIQ&t=0s)


# Popover


```swift
    @State var showNewScreen: Bool = false

newScreen2(showNewScreen: $showNewScreen)
                .padding(.top, 100)
                .offset(y: showNewScreen ? 0 : UIScreen.main.bounds.height)
                .animation(.spring())
            
}
```
[Youtube Tutorial](https://www.youtube.com/watch?v=5QDvfNQF304&t=0s)
