
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

---

## Font Sizes
```swift
                    Text("Large Title")
                        .font(.largeTitle)
                    Text("Title")
                        .font(.title)
                    Text("Title 2")
                        .font(.title2)
                    Text("Title 3")
                        .font(.title3)
                    Text("Headline")
                        .font(.headline)
                    Text("Subheadline")
                        .font(.subheadline)
                    Text("Body")
                        .font(.body)
                    Text("Callout")
                        .font(.callout)
                    Text("Footnote")
                        .font(.footnote)
                    Text("Caption")
                        .font(.caption)
                    Text("Caption 2")
                        .font(.caption2)
                
```

---

## Weights

```swift
 Section{
                Text("Ultra Light")
                    .font(.body)
                    .fontWeight(.ultraLight)
                Text("Thin")
                    .font(.body)
                    .fontWeight(.ultraLight)
                Text("Light")
                    .font(.body)
                    .fontWeight(.light)
                Text("Regular")
                    .font(.body)
                    .fontWeight(.thin)
                Text("Medium")
                    .font(.body)
                    .fontWeight(.medium)
                Text("Semi Bold")
                    .font(.body)
                    .fontWeight(.semibold)
                Text("Bold")
                    .font(.body)
                    .fontWeight(.bold) // or .bold()
                Text("Heavy")
                    .font(.body)
                    .fontWeight(.heavy)
                Text("Black")
                    .font(.body)
                    .fontWeight(.black)
```

---

## Lines
```swift

                Text("Underline Color")
                    .underline(color: .red)
                Text("Strikethrouhg Color")
                    .strikethrough(color: .green)


                    Text("This is the first line.\nThis is the second line.")

   ```

---

## System

```swift
                Text("System - Monospaced ")
                    .font(.system(size: 24, weight: .semibold, design: .monospaced))
                Text("System - Rounded ")
                    .font(.system(size: 24, weight: .semibold, design: .rounded))
                Text("System - Serif ")
                    .font(.system(size: 24, weight: .semibold, design: .serif))
   ```

---

## Formatting
```swift
              Text("Multi Line Text Alignment - Multi Line Text Alignment - Multi Line Text Alignment")
                    .multilineTextAlignment(.leading)
                Text("""
                     shows
                     multiple
                     lines
                     """)
                Text("Baseline Offset / Line Spacing. +25 space below each line, -25 space above each line ")
                    .baselineOffset(25.0) //
                    .multilineTextAlignment(.leading)
                Text("Kerning (Letter spacing)")
                    .kerning(10)
                Text("MinimumScaleFactor, allows text to scale down to fit frame, 0.1 = allow scale down down to 10%")
                    .minimumScaleFactor(0.1)
                Text("Leading")
                    .frame(alignment: .leading)
                Text("Foreground Color (Font Color)")
                    .foregroundColor(.red)
                Text("Inspector Additions")
                    .italic()
```

---

## Case
```swift
                Text("Capitalized".capitalized)
                Text("Lowercased".lowercased())
                Text("uppercased".uppercased())
```
