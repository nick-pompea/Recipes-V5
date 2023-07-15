# Control Flow



| if | ![Screenshot 2023-07-15 at 11 54 34 AM](https://github.com/nick-pompea/Recipes-V5/assets/123673749/dfaf3bdb-65bc-435e-9be9-207dcbd6443e) | 
| --- | --- | 

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

| Ternary Operator | ![Screenshot 2023-07-15 at 11 57 37 AM](https://github.com/nick-pompea/Recipes-V5/assets/123673749/5949eca3-c046-46b8-af9c-d58c508ee015) | 
| --- | ----------- |




```swift
Color(isLoading ? Color.black : Color.red)
```
[Youtube Tutorial](https://www.youtube.com/watch?v=xzFSOdpxy-o&t=0s)

---



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

| if let | ![Screenshot 2023-07-15 at 12 02 16 PM](https://github.com/nick-pompea/Recipes-V5/assets/123673749/4f31ec2c-8dd3-47c8-b856-9feeea268b9a) | 
| --- | --- | 

```swift
if let text = displayText {
Text(text)
}
```
---

| Switch | ![Screenshot 2023-07-15 at 12 03 14 PM](https://github.com/nick-pompea/Recipes-V5/assets/123673749/ac2cc667-0387-4877-b2ff-64a2ff828ff0) | 
| --- | --- | 

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


| do catch | ![Screenshot 2023-07-15 at 12 01 18 PM](https://github.com/nick-pompea/Recipes-V5/assets/123673749/a7b90428-750c-424f-aa9a-6cce9bb1b253) | 
| --- | --- |

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




