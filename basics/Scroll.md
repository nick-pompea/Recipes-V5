# Scrolling

ScrollView
```swift
ScrollView (.vertical, showsIndicators: true){
}

ScrollView (.horizontal, showsIndicators: false){
}


```
[Youtube Tutorial](https://www.youtube.com/watch?v=9QhhpeYKjOs&t=0s)


---

## Scroll View Reader
```swift

import SwiftUI

struct ScrollViewReaderView: View {
    @State var textFeildText: String = ""
    @State var scrollToIndex: Int = 0
    var body: some View {
        VStack {
            TextField("Enter numner", text: $textFeildText)
                .frame(height: 55)
                .border(Color.gray)
                .padding(.horizontal)
                .keyboardType(.numberPad)
            
            Button("Scroll Now") {
                withAnimation(.spring()) {
                    if let index = Int(textFeildText) {
                        scrollToIndex = index
                    }
                   // proxy.scrollTo(30, anchor: .top)
                }
            }
            
            ScrollView{
                ScrollViewReader { proxy in
                   
                    
                    ForEach( 0..<50) { index in
                        Text("This is item number: \(index)")
                            .font(.headline)
                            .frame(height: 200)
                            .frame(maxWidth: .infinity)
                            .background(Color.white)
                            .cornerRadius(10)
                            .shadow(radius: 10)
                            .padding()
                            .id(index)
                    }
                    .onChange(of: scrollToIndex) { newValue in
                        withAnimation(.spring()) {
                            proxy.scrollTo(newValue, anchor: .top)
                        }
                    }
                }
            }
        }
    }
}

struct ScrollViewReaderView_Previews: PreviewProvider {
    static var previews: some View {
        ScrollViewReaderView()
    }
}
}
```
[Youtube Tutorial](https://www.youtube.com/watch?v=ZkOvD3okAJo&t=0s)
