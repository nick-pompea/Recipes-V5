# Push Notifications

* Imports 
```swift
import SwiftUI
import UserNotifications
// if needed from example 
import CoreLocation
```
* Manager
```swift

class NotificationManager {
    static let instance = NotificationManager()
    
    func requestAuthorization() {
        let options: UNAuthorizationOptions = [.alert, .sound, .badge]
        UNUserNotificationCenter.current().requestAuthorization(options: options) { (success, error) in
            if let error = error {
                print("error \(error)")
            } else {
                print("success")
            }
        }
    }
    
    func scheduleNotifcation() {
        let constant = UNMutableNotificationContent()
        constant.title = "This is my first notification"
        constant.subtitle = "This is subtitle"
        constant.sound = .default
        constant.badge = 1

        var dateComponents = DateComponents()
        dateComponents.hour = 11
        dateComponents.minute = 0
        dateComponents.weekday = 2 // 1= Sunday

        _ = UNCalendarNotificationTrigger(dateMatching: dateComponents, repeats: true)
    }
    
    func cancelNotifcaitons() {
        UNUserNotificationCenter.current().removeAllPendingNotificationRequests()
        UNUserNotificationCenter.current().removeAllDeliveredNotifications()

    }
    
}

```

Example
```swift
        VStack{
            Button("Request Permission") {
                NotificationManager.instance.requestAuthorization()
            }
            
            Button("Cancel Notification") {
                NotificationManager.instance.cancelNotifcaitons()
            }
            
            Button("Schedule Notification") {
                NotificationManager.instance.scheduleNotifcation()
            }
            .onAppear{
                UIApplication.shared.applicationIconBadgeNumber = 0
            }
        }


```

[Youtube Tutorial](https://www.youtube.com/watch?v=mG9BVAs8AIo&t=0s)
