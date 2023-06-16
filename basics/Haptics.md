# Haptics

* Manager
```swift
class hapticManager {
    
    static let instance = hapticManager() //Singlton
    
    func notification(type: UINotificationFeedbackGenerator.FeedbackType) {
        let generattor = UINotificationFeedbackGenerator()
        generattor.notificationOccurred(type)
    }
    
    func impact(style: UIImpactFeedbackGenerator.FeedbackStyle) {
        let generator = UIImpactFeedbackGenerator(style: style)
        generator.impactOccurred()
    }
}

* Examples
```swift
VStack(spacing: 20){
            Button {
                hapticManager.instance.notification(type: .error)
            } label: {
                Text("error")
            }
            
            Button {
                hapticManager.instance.notification(type: .success)
            } label: {
                Text("success")
            }
            
            Button {
                hapticManager.instance.notification(type: .warning)
            } label: {
                Text("warning")
            }

            
            Divider()
            
            Button {
                hapticManager.instance.impact(style: .heavy)
            } label: {
                Text("heavy")
            }
            
            Button {
                hapticManager.instance.impact(style: .medium)
            } label: {
                Text("medium")
            }
            
            Button {
                hapticManager.instance.impact(style: .rigid)
            } label: {
                Text("rigid")
            }
            
            Button {
                hapticManager.instance.impact(style: .light)
            } label: {
                Text("light")
            }
            
            Button {
                hapticManager.instance.impact(style: .soft)
            } label: {
                Text("soft")
            }
            
            Button {
                hapticManager.instance.impact(style: .heavy)
            } label: {
                Text("heavy")
            }
            
            
            
        }


```

```
[Youtube Tutorial](https://www.youtube.com/watch?v=H45bl6e0cNs&t=0s)

