
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
[Youtube Tutorial](https://www.youtube.com/watch?v=0H4G3lGnJE0&t=0s)


---

## MatchedGeometry Effect 

Modifiers
```swift
@Namespace private var animation
//
 .matchedGeometryEffect(id: "text", in: animation)
```

Example
```swift
import SwiftUI

struct matchedGeometryEffectView: View {
    @Namespace private var animation
    @State private var isFlipped = false
    var body: some View {
        VStack{
            if isFlipped {
                Circle()
                    .fill(Color.red)
                    .frame(width: 44, height: 44)
                    .matchedGeometryEffect(id: "Shape", in: animation)
                Text("Hello, World!")
                    .font(.headline)
                    .matchedGeometryEffect(id: "text", in: animation)
            } else {
                Text("Hello, World!")
                    .matchedGeometryEffect(id: "text", in: animation)
                Circle()
                    .fill(Color.red)
                    .frame(width: 44, height: 44)
                    .matchedGeometryEffect(id: "Shape", in: animation)
            }
        }
        .onTapGesture {
            withAnimation {
                isFlipped.toggle()

            }
        }
    }
}

struct matchedGeometryEffectView_Previews: PreviewProvider {
    static var previews: some View {
        matchedGeometryEffectView()
    }
}
```

[Youtube Tutorial](https://www.youtube.com/watch?v=x7fdvXdVd98)

