# Timer and onReceive


```swift
let timer = Timer.publish(every: 2.0, on: .main, in: .common).autoconnect()
 //
.onReceive(timer) { value in
}
```

notes
```swift

    // current time
    /*
     @State var currentDate: Date = Date()
     var dateFormatter: DateFormatter {
     let formatter = DateFormatter()
     formatter.timeStyle = .medium
     return formatter
     }
     */
    
    // count down
    /*
     @State var count: Int = 10
     @State var finishedText: String? = nil
     */
    
    // count down to date
    /*
     @State var timeRemaining: String = ""
     let futureDate: Date = Calendar.current.date(byAdding: .hour, value: 1, to: Date()) ?? Date()
     
     func updateTimeRemaining() {
     let remaining = Calendar.current.dateComponents([.hour, .minute, .second], from: Date(), to: futureDate)
     let hour = remaining.hour ?? 0
     let minute = remaining.minute ?? 0
     let second = remaining.second ?? 0
     timeRemaining = "\(hour):\(minute):\(second)"
     }
     */
```

[Youtube Tutorial](https://www.youtube.com/watch?v=ymXRX6ZB-J0&t=0s)

