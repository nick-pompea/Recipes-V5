
# Gestures

 [Long Press Gesture](basics/Gesture.md)
---

## Magnification
* Modifier
```swift
            Rectangle()
                .scaleEffect(1 + currentAmount)
//
                .gesture(
                    MagnificationGesture()
                        .onChanged {value in
                            currentAmount = value - 1
                            
                        }
                        .onEnded {value in
                            withAnimation(.spring()) {
                                currentAmount = 0
                            }
                        }
                )
```
[Youtube Tutorial](https://www.youtube.com/watch?v=RkfJoNzfJ8w&t=0s)
---
## Rotation
* Modifier
```swift
            Rectangle()
            .rotationEffect(angle)
//
            .gesture(
                RotationGesture()
                    .onChanged { value in
                        angle = value
                    }
                    .onEnded({ value in
                        withAnimation(.spring()){
                            angle = Angle(degrees: 0)
                        }
                    })
            )
```
[Youtube Tutorial](https://www.youtube.com/watch?v=RkfJoNzfJ8w&t=0s)
---
## Drag
* Modifier
```swift    
@State var offset: CGSize = CGSize(width: 0, height: 0)
//
            RoundedRectangle(cornerRadius: 20)
                .frame(width: 300, height: 500)
                .offset(offset)
//
                .gesture(
                    DragGesture()
                    .onChanged { value in
                        withAnimation(.spring()) {
                            offset = value.translation
                        }
                    }
                    .onEnded { value in
                        withAnimation(.spring()) {
                            offset = CGSize(width: 0, height: 0)
                        }
                    }
            )
```
* Card Example
```swift    

import SwiftUI

struct DragGestureView: View {
    
    @State var offset: CGSize = CGSize(width: 0, height: 0)
    
    
    var body: some View {
    
        ZStack {
            VStack{
                Text("\(offset.width)")
                Spacer()
            }
            RoundedRectangle(cornerRadius: 20)
                .frame(width: 300, height: 500)
                .offset(offset)
                .scaleEffect(getScaleAmount())
                .rotationEffect(Angle(degrees: getRotationaAmount()))
                .gesture(
                    DragGesture()
                    .onChanged { value in
                        withAnimation(.spring()) {
                            offset = value.translation
                        }
                    }
                    .onEnded { value in
                        withAnimation(.spring()) {
                            offset = CGSize(width: 0, height: 0)
                        }
                    }
            )
        }
    }
    
    func getScaleAmount() -> CGFloat {
        let max = UIScreen.main.bounds.width / 2
        let currantAmount = abs(offset.width)
        let percent = currantAmount / max
        let minimum = min(percent, 0.5) * 0.5
        return 1.0 - minimum
    }
    
    func getRotationaAmount() -> Double {
        let max = UIScreen.main.bounds.width / 2
        let currentAmount = offset.width
        let percent = currentAmount / max
        let percentAsDouble = Double(percent)
        let maxAngle: Double = 10
        return percentAsDouble * maxAngle
    }
}

struct DragGestureView_Previews: PreviewProvider {
    static var previews: some View {
        DragGestureView()
    }
}
```


[Youtube Tutorial](https://www.youtube.com/watch?v=O3QAI8Mxh8M)
---
