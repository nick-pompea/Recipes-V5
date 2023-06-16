# Mask


Rating Example
```swift
import SwiftUI

struct MaskView: View {
    @State var rating: Int = 0
    var body: some View {
        ZStack{
            starView
                .overlay(overlayView)
                .mask(starView)
            
                }
                }
    
    
    private var overlayView: some View {
        GeometryReader { geo in
            ZStack(alignment: .leading){
                Rectangle()
                   .foregroundColor(Color.yellow)
                    .frame(width: CGFloat(rating) / 5 * geo.size.width)
            }
        }
        .allowsHitTesting(false)
    }

    
    
    private var starView: some View {
        HStack{
            ForEach(1..<6) { i in
                Image(systemName: "star.fill")
                    .font(.largeTitle)
                    .foregroundColor(.gray)
                    .onTapGesture {
                        withAnimation(.easeOut) {
                        rating = i
                    }
                }
            }
        }
    }
}

struct MaskView_Previews: PreviewProvider {
    static var previews: some View {
        MaskView()
    }
}


```
[Youtube Tutorial](https://www.youtube.com/watch?v=pxx1ueCbnls&t=0s)

