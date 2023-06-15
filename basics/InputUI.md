
# Input UI

## Toggle


```swift
    @State var toggleIsOn: Bool = false

      Toggle(
                isOn: $toggleIsOn,
                label: {
                Text("Toggle")
                })

```


Modifiers
```swift
            .toggleStyle(SwitchToggleStyle(tint: Color(#colorLiteral(red: 0, green: 0.9914394021, blue: 1, alpha: 1))))
```
[Youtube Tutorial](https://www.youtube.com/watch?v=JIT8sL_VtNA&t=0s)


---
