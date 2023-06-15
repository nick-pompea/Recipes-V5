
# Alerts

Default
```swift
.alert(isPresented: $showAnotherAlertHere) {   
Alert(
            title: Text(alertTitle),
            message: Text(alertMessage),
            dismissButton: .default(Text("OK"))
            )
 }

```

Example with diffrent alerts 
```swift

import SwiftUI

struct AlertsView: View {
    @State var showAlert: Bool = false
    @State var bgColor: Color = .yellow
    @State var alertTitle: String = ""
    @State var alertMessage: String = ""
    @State var showAnotherAlertHere: Bool = false
    @State var alertsEnum: MyAlertsEnum? = nil
    @State var alertsEnumBool: Bool = false

    
    enum MyAlertsEnum {
        case success
        case error
        
    }


    var body: some View {
        ZStack{
            bgColor.edgesIgnoringSafeArea(.all)
            
            VStack(spacing: 20){
                Button("Button 1"){
                    alertTitle = "Error with upload☹️"
                    alertMessage = "The file could not be uploaded"
                    showAnotherAlertHere.toggle()
                }
                .alert(isPresented: $showAnotherAlertHere) {
                    getAnotherAlert()
                }
                
                
                Button("Button 2"){
                    alertTitle = "Complted: Upload  ✅"
                    alertMessage = "Fully uploaded"

                    showAnotherAlertHere.toggle()
                }
                .alert(isPresented: $showAnotherAlertHere) {
                    getAnotherAlert()
                }
                
                
                Button("Button 3"){
                    showAlert.toggle()
                }
                .alert(isPresented: $showAlert) {
                    getAlert()
                }
                
                Button("Button 4"){
                    alertsEnum = .error
                    alertsEnumBool.toggle()
                }
                .alert(isPresented: $alertsEnumBool) {
                    getAlertsEnum()
                }
                
                Button("Button 5"){
                    alertsEnum = .success
                    alertsEnumBool.toggle()

                }
                .alert(isPresented: $alertsEnumBool) {
                    getAlertsEnum()

                }
                
                
            }
        }
    }
    func getAnotherAlert() -> Alert {
        return Alert(
            title: Text(alertTitle),
            message: Text(alertMessage),
            dismissButton: .default(Text("OK"))
            )
    }
    
   
    func getAlert() -> Alert {
        return Alert(
            title: Text("This is the title"),
            message: Text("Message for the error"),
            primaryButton: .destructive(Text("Delete"), action: {
                bgColor = Color.red
            }),
            secondaryButton: .cancel())
    }
    
    func getAlertsEnum() -> Alert{
        switch alertsEnum{
        case .error:
            return Alert(title: Text("There was an error"))
        case .success:
            return Alert(title: Text("Success"))
        default:
            return Alert(title: Text("Error"))

        }
    }
    
    
    
}

struct AlertsView_Previews: PreviewProvider {
    static var previews: some View {
        AlertsView()
    }
}

```

[Youtube Tutorial](https://www.youtube.com/watch?v=dEmySJwCreo&t=0s)
