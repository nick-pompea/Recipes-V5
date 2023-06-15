
# Animations

Put animation around changing variable
```swift
withAnimation(Animation
.default
isAnimated.toggle()
}
```

Modifier
```swift
.animation(.spring(
response: 0.5,
dampingFraction: 0.7,
blendDuration: 1.0)
)
}


```

Example
```swift
import SwiftUI

struct AnimationsView: View {
    
    @State var isAnimated: Bool = false
    
    var body: some View {
        VStack{
            Button("Button") {
                withAnimation(Animation
                    .default
                    .repeatCount(5, autoreverses: false)
                                ) {
                    isAnimated.toggle()
                }
            }
            Spacer()
            RoundedRectangle(cornerRadius: isAnimated ? 50 : 25)
                .fill(isAnimated ? Color.red : Color.green)
                .frame(
                    width: isAnimated ? 100 : 300,
                    height: isAnimated ? 100 : 300,
                    alignment: .center)
                .rotationEffect(Angle(degrees: isAnimated ? 360 : 0))
                .offset(y: isAnimated ? 300 : 0)
            
            
            
            Spacer()
        }
    }
}

struct AnimationsView_Previews: PreviewProvider {
    static var previews: some View {
        AnimationsView()
    }
}


```
[Youtube Tutorial](https://www.youtube.com/watch?v=0WY-wrW2_bs&t=0s)
