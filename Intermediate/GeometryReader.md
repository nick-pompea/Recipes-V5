
# Geometry Reader

```swift
import SwiftUI

struct GeometryReaderView: View {
    var body: some View {
        ScrollView(.horizontal, showsIndicators: false) {
            HStack{
                ForEach(0..<20) { index in
                    GeometryReader{ geo in
                        RoundedRectangle(cornerRadius: 20)
                            .rotation3DEffect(
                                Angle(degrees: getPercentage(geo: geo) * 40),
                                axis: (x: 0.0, y: 1.0, z: 0.0))
                }
                    .frame(width: 300, height: 250)
                    .padding()
            }
            }
        }
 }
    func getPercentage(geo: GeometryProxy) -> Double {
        let maxDistacne = UIScreen.main.bounds.width / 2
        let cuttntX = geo.frame(in: .global).midX
        return Double(1 - (cuttntX / maxDistacne))
        
    }
}

struct GeometryReaderView_Previews: PreviewProvider {
    static var previews: some View {
        GeometryReaderView()
    }
}


```
[Youtube Tutorial](https://www.youtube.com/watch?v=lMteVjlOIbM&t=0s)
