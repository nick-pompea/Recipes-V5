
# Grids

GridItems
```swift
GridItem(.flexible())
GridItem(.fixed(75))
GridItem(.adaptive(minimum: 150, maximum: 300))
```

Can be used in an array

flexible
```swift
    let columns: [GridItem] = [
        GridItem(.flexible(), spacing: nil, alignment: nil),
        GridItem(.flexible(), spacing: nil, alignment: nil),
        GridItem(.flexible(), spacing: nil, alignment: nil)
]
```

adaptive
```swift
    let columns: [GridItem] = [
            GridItem(.adaptive(minimum: 150, maximum: 300 ), spacing: nil, alignment: nil)),
            GridItem(.adaptive(minimum: 150, maximum: 300 ), spacing: nil, alignment: nil)),
]
```
fixed
```swift
    let columns: [GridItem] = [
            GridItem(.fixed(75), spacing: nil, alignment: nil),
            GridItem(.fixed(100), spacing: nil, alignment: nil),
            GridItem(.fixed(75), spacing: nil, alignment: nil),
            GridItem(.fixed(50), spacing: nil, alignment: nil)
]
```

## Lazy

* Doesn't load until needed

LazyVGrid
```swift
  LazyVGrid() {
  }
  
  LazyVGrid(
                columns: columns,
                alignment: .center,
                spacing: 6,
                pinnedViews: [.sectionHeaders],
                content: {
                
                }

```

Header  
* Example 
```swift
  Section(header:
                        Text("Section 1")
                        .background(Color.blue)
                        .font(.title)
                        .foregroundColor(.white)
                        .frame(maxWidth: .infinity, alignment: .leading)
                        .background(Color.blue)
                        .padding()
                        .background(Color.blue)
                    
             ) 

```

# Instagra m
```swift
import SwiftUI

struct Grids: View {
    
    let columns: [GridItem] = [
        GridItem(.flexible(), spacing: nil, alignment: nil),
        GridItem(.flexible(), spacing: nil, alignment: nil),
        GridItem(.flexible(), spacing: nil, alignment: nil)    
    ]
    
    var body: some View {
        ScrollView{
            
            Rectangle()
                .fill(Color.orange)
                .frame(height: 400)
            
            LazyVGrid(
                columns: columns,
                alignment: .center,
                spacing: 6,
                pinnedViews: [.sectionHeaders],
                content: {
                    
                    Section(header:
                        Text("Section 1")
                        .background(Color.blue)
                        .font(.title)
                        .foregroundColor(.white)
                        .frame(maxWidth: .infinity, alignment: .leading)
                        .background(Color.blue)
                        .padding()
                        .background(Color.blue)
                    
                    ) {
                    
                        ForEach(0..<20) {i in
                            Rectangle()
                                .frame(height: 150)
                        }
                    }
                    Section(header:
                                Text("Section 2")
                                .foregroundColor(Color.white)
                                .font(.title)
                                .frame(maxWidth: .infinity, alignment: .leading)
                                .background(Color.red)
                                .padding()
                                .background(Color.red)
                    
                    ) {
                    
                        ForEach(0..<20) {i in
                            Rectangle()
                                .fill(Color.green)
                                .frame(height: 150)
                        }
                    }
            })
        }
    }
}

struct Grids_Previews: PreviewProvider {
    static var previews: some View {
        Grids()
    }
}

```



[Youtube Tutorial](https://www.youtube.com/watch?v=vHvb7LH8VuE&t=0s)

