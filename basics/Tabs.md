
# Tabs


```swift
  struct ContentView: View {
    @State private var selectedTab = "One"
    
    var body: some View {
        TabView(selection: $selectedTab) {
            Text("Tab 1")
                .onTapGesture {
                    selectedTab = "Two"
                }
                .tabItem {
                    Label("One", systemImage: "star")
                }
                .tag("One")

            Text("Tab 2")
                .tabItem {
                    Label("Two", systemImage: "circle")
                }
                .tag("Two")
        }
    }
}
        
        // For loop
        
                TabView{
            ForEach(icons, id: \.self) {i in
                Image(systemName: i)
                    .resizable()
                    .scaledToFit()
                    .padding(30)
            }
        }
        
        


```



Modifiers
```swift
        .tabViewStyle(PageTabViewStyle())



```

![Tabs](https://github.com/nick-pompea/Recipes-V5/assets/123673749/8cf28d51-3229-4162-9768-b53e9373d36b)


[Youtube Tutorial](https://www.youtube.com/watch?v=5E_D9D8Z5nQ&t=0s)

Fancy 
[Youtube Tutorial](https://www.youtube.com/watch?v=5E_D9D8Z5nQ&t=0s)
