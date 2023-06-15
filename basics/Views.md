# Views

Basic view
```swift
struct BasicView: View {
    var body: some View {

}
}
```
Pass Views

* Example
```swift

import SwiftUI

struct ExtractingView: View {
    
 @State var backgroundColor: Color = .pink
    
    
    var body: some View {
        ZStack{
            // background
            backgroundColor
                .ignoresSafeArea()

            
            //content
            contentLayer
        }
    }
 
    // logic extraction
    
    
    var contentLayer: some View{
        VStack{
            Text("Title")
                .font(.largeTitle)
            
            Button(action: {
                buttonPressed()

            }, label: {
                Text("Press Me")
                    .font(.headline)
                    .foregroundColor(Color.white)
                    .padding()
                    .background(Color.black)
                    .cornerRadius(10)
            })
        }
    }
    
    func buttonPressed() {
        backgroundColor = .yellow
}
    
    
    
    
}

struct ExtractingView_Previews: PreviewProvider {
    static var previews: some View {
        ExtractingView()
    }
}
```
[Youtube Tutorial](https://www.youtube.com/watch?v=pIUBC6wZjpM&t=0s)

