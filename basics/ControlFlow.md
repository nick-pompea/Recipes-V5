# Control Flow

if 
```swift
@State var isLoading: Bool = false
---
if isLoading {
ProgressView()
}
```
---
if else
```swift
@State var isLoading: Bool = false

if isLoading {
ProgressView()
} else {
MainView()
}
```
[Youtube Tutorial](https://www.youtube.com/watch?v=W8sGT16WAkQ&t=0s)

---

Ternary Operator
```swift
Color(isLoading ? Color.black : Color.red)
```
[Youtube Tutorial](https://www.youtube.com/watch?v=xzFSOdpxy-o&t=0s)

Guard
* https://www.programiz.com/swift-programming/guard-statement
```swift
guard expression else {
  // statements
  // control statement: return, break, continue or throw.
}
```
---
Guard Let
```swift
    func loadDataTwo() {
        guard let userID = currentUserID else {
            displayText = "Error no user ID"
            return
        }
        isLoading = true
        DispatchQueue.main.asyncAfter(deadline: .now() + 3) {
            displayText = "This is the new data, User ID is: \(userID)"
            isLoading = false
        }
    }
```
* [Youtube Tutorial](https://www.youtube.com/watch?v=wmQIl0O9HBY&t=0s)

---
if let
```swift
if let text = displayText {
Text(text)
}
```
---

Switch
```swift
        switch alertsEnum{
        case .error:
            return Alert(title: Text("There was an error"))
        case .success:
            return Alert(title: Text("Success"))
        default:
            return Alert(title: Text("Error"))
        }
```
---
do catch
```swift
do {
        // Code
        } catch {
        // Error
}
```
do try catch
* Example
```swift
        do {
            let NewTitle = try? manager.getTitleThree()
            if let NewTitle = NewTitle {
                self.text = NewTitle
            }
            let finalTitle = try manager.getTitleFour()
            self.text = finalTitle

        } catch {
            self.text = error.localizedDescription
        }
}

```
[Youtube Tutorial](https://www.youtube.com/watch?v=ss50RX7F7nE)
---




