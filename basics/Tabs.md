
# Tabs


```swift
        TabView(selection: $selectedTab) {
            HomeView(selectedTab: $selectedTab)
                .tabItem {
                Image(systemName: "house.fill")
                Text("Home")
                }.tag(0)
            Text("Browse Tab").tabItem {
                Image(systemName: "globe")
                Text("Browse")
            }.tag(1)
            Text("Profile Tab").tabItem {
                Image(systemName: "person.fill")
                Text("Profile")
            }.tag(2)
        }


```

![Tabs](https://github.com/nick-pompea/Recipes-V5/assets/123673749/8cf28d51-3229-4162-9768-b53e9373d36b)


[Youtube Tutorial](https://www.youtube.com/watch?v=5E_D9D8Z5nQ&t=0s)
