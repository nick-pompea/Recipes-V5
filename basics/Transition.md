
# Transitions

Modifiers
```swift
.transition(.asymmetric(
insertion: .move(edge: .bottom),
removal: AnyTransition.opacity.animation(.easeInOut)
                    ))
```

Example
```swift
import SwiftUI

struct TransitionView: View {
    
    @State var showView: Bool = false
    
    var body: some View {
        ZStack(alignment: .bottom) {
            
         
            VStack{
                Button("Button") {
                    showView.toggle()
                }
                Spacer()
            }
            
            if showView {
                RoundedRectangle(cornerRadius: 30)
                    .frame(height: UIScreen.main.bounds.height * 0.5)
                    //.transition(.move(edge: .bottom))
                  //  .transition(AnyTransition.scale .animation(.easeInOut))
                    .transition(.asymmetric(
                        insertion: .move(edge: .bottom),
                        removal: AnyTransition.opacity.animation(.easeInOut)
                                
                                //.move(edge: .bottom)
                    ))
                    .animation(.easeInOut)
                
            }
        }
        .edgesIgnoringSafeArea(.bottom)
    }
}

struct TransitionView_Previews: PreviewProvider {
    static var previews: some View {
        TransitionView()
    }
}
```


[Youtube Tutorial](https://www.youtube.com/watch?v=X6FAIa0nJoA&t=0s)
