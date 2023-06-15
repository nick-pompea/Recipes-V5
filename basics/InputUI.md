
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

## Picker


```swift
    @State var pickerSelection: String = "1"

                Picker(
                    selection: $pickerSelection,
                    label: Text("Picker"),
                    content: {
                        ForEach(18..<99) {i in
                            Text("\(i)")
                                .font(.title)
                                .foregroundColor(.red)
                                .tag("\(i)")
                        }
                    })
```

Modifiers
```swift
               .pickerStyle(WheelPickerStyle())
               .pickerStyle(MenuPickerStyle())
               .pickerStyle(SegmentedPickerStyle())
```

[Youtube Tutorial](https://www.youtube.com/watch?v=2pSDE56u2F0&t=0s)
