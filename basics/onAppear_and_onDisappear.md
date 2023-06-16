
# On Appear

```swift
          .onAppear(perform: {

                }
            })


```

# On Disappear
```swift
          .onDisappear(perform: {
      
          })


```


Example
```swift

import SwiftUI

struct onAppear_and_onDisappear: View {
    @State var myText: String = "Starting"
    @State var coint: Int = 0
    var body: some View {
        NavigationView{
            ScrollView{
                Text(myText)
                LazyVStack{
                    ForEach(0..<50){ i in
                        RoundedRectangle(cornerRadius: 25)
                            .frame(height: 200)
                            .padding()
                            .onAppear {
                                coint += 1
                            }
                            
                    }
                }
            }
            .onAppear(perform: {
                DispatchQueue.main.asyncAfter(deadline: .now() + 5) {
                    myText = "New text"
                }
            })
            
//            .onDisappear(perform: {
//                myText = "Ending text"
//            })
            
            .navigationTitle("On Appear: \(coint)")
        }
    }
}

struct onAppear_and_onDisappear_Previews: PreviewProvider {
    static var previews: some View {
        onAppear_and_onDisappear()
    }
}
```

[Youtube Tutorial](https://www.youtube.com/watch?v=QAP4DbfoKvk&t=0s)
