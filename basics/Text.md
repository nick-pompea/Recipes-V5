
# Text

Basic
```swift
Text("Hello")
```

## TextField

```swift
@State var textFeild: String = ""

TextField("Type here ...", text: $textFeild)
```

Modifiers
```swift
.textFieldStyle(RoundedBorderTextFieldStyle())
```

[Youtube Tutorial](https://www.youtube.com/watch?v=-_-BNwUZrrc&t=0s)



## TextEditor

```swift
 @State var textEditorText: String = "Write your bio here ......"

TextEditor(text: $textEditorText)

```


[Youtube Tutorial](https://www.youtube.com/watch?v=NiiYeoFYiXQ&t=0s)

---

## Basic Styling

```swift
 "**Bold**"
 "_Italic_"
 "Base\(StringInterpolation)"
 """
 Multiple
 Lines
 """
```
