
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

---


## Color Picker


```swift
    @State var color: Color = .green

            ColorPicker("Select a color",
                        selection: $color,
                        supportsOpacity: true
                        )
```
[Youtube Tutorial](https://www.youtube.com/watch?v=nUlY2RYHV9U&t=0s)


---
## Date Picker


```swift
    @State var selectaDate: Date = Date()
    
    DatePicker("Select a Date", selection: $selectaDate, in: startingDate...endingDate)

```

Styles
```swift
           GraphicalDatePickerStyle()
           WheelDatePickerStyle()
           DefaultDatePickerStyle()
```

[Youtube Tutorial](https://www.youtube.com/watch?v=EnNAQ-b1yPU&t=0s)

---


## Stepper


```swift
      @State var steperValue: Int = 10

     Stepper("Stepper: \(steperValue)", value: $steperValue)

```

With Increment
```swift
    @State var withIncrement: CGFloat = 0

            Stepper("Stepper 2: \(steperValue)"){
                withIncrement += 25
            } onDecrement: {
                withIncrement += -25
            }
```

[Youtube Tutorial](https://www.youtube.com/watch?v=T7inPesyOY8&t=0s)

---
