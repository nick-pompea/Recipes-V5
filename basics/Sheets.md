# Sheets

* Can only use on for each view 

Modifiers
```swift
.sheet(isPresented: $showSheet) {
secondScreen()
}
```

# FullScreenCover

Modifiers
```swift
.fullScreenCover(isPresented: $showSheet) {
secondScreen()
}
```
[Youtube Tutorial](https://www.youtube.com/watch?v=ddr3E0l4gIQ&t=0s)


# Popover


```swift
    @State var showNewScreen: Bool = false

newScreen2(showNewScreen: $showNewScreen)
                .padding(.top, 100)
                .offset(y: showNewScreen ? 0 : UIScreen.main.bounds.height)
                .animation(.spring())
            
}
```
[Youtube Tutorial](https://www.youtube.com/watch?v=5QDvfNQF304&t=0s)


# Action Sheets
```swift
.actionSheet(isPresented: $showActionSheet, content: getActionSheet) 
}
```
func
```swift
    func getActionSheet() -> ActionSheet {
        
        let shareButton: ActionSheet.Button = .default(Text("Share")){
            //add code to share post
        }
        let reportButton: ActionSheet.Button = .destructive(Text("Report")){
            //add code to share post
        }
        let deleteButton: ActionSheet.Button = .destructive(Text("Delete")){
            //add code to delete
        }
        let cancelButton: ActionSheet.Button = .cancel()
        
        let titleText = Text("What would you like to do")

        switch actionSheetOption {
        case .isOtherPost:
            return ActionSheet(
                            title: titleText,
                            message: nil,
                            buttons: [shareButton, reportButton, cancelButton])
        case .isMyPost:
            return ActionSheet(
                            title: titleText,
                            message: nil,
                            buttons: [shareButton, reportButton, deleteButton, cancelButton])
            }
        }
}
```

[Youtube Tutorial](https://www.youtube.com/watch?v=tNwnihqJf2I&t=0s)

