# Navigation

Default
```swift
 NavigationView {
 }
```

Modifiers
```swift
            .navigationTitle("Navigation Title")
            .navigationBarTitleDisplayMode(.automatic)
            .navigationBarHidden(true)
```

Navigation Bar Items
```swift
            .navigationBarItems(
                leading:
                    HStack{
                        
                        Image(systemName: "person.fill")

                        Image(systemName: "flame.fill")

                    },
                trailing:
                    NavigationLink(destination: {
                    myOtherScreen()
                }, label: {
                    Image(systemName: "gear")
                })
                    .accentColor(.red)
            )
```
Nav Links
```swift
NavigationLink("Hello World",destination: myOtherScreen())
```



[Youtube Tutorial](https://www.youtube.com/watch?v=tXFwyFdkSas&t=0s)

