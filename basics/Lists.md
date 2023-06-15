
# Lists

Default
```swift
 List{
 }
```
Modifiers
```swift
.onDelete { IndexSet in
delete(IndexSet: IndexSet)
.onMove(perform: moveRow)
.listRowBackground(Color.pink)
.padding(.vertical)
}
```
funcs for Modifiers
```swift
    func delete(IndexSet: IndexSet) {
        fuits.remove(atOffsets: IndexSet)
    }
    
    func moveRow(indices: IndexSet, toOffset: Int) {
        fuits.move(fromOffsets: indices, toOffset: toOffset)

    }
```


Style
```swift
            .listStyle(
                //SidebarListStyle()
                //PlainListStyle()
                //InsetGroupedListStyle()
                DefaultListStyle()
               // GroupedListStyle()
            )
}
```

Example 
```swift
import SwiftUI

struct ListViews: View {
    
    @State var fuits: [String] = [
        "Apple", "Orange", "Bannana", "Peach"
    ]
    @State var veggie: [String] = [
        "Tomato", "Potato", "Carrot", "Other"
    ]
    
    
    var body: some View {
        
        NavigationView() {
            List{
                Section(header:
                            HStack{
                            Text("Fruits")
                                 Image(systemName: "flame.fill")
                                 }
                    .font(.headline)
                    .foregroundColor(.orange)
                                ){
                    ForEach(fuits, id: \.self) {i in
                        Text(i)
                            .font(.caption)
                            .foregroundColor(.black)
                           // .frame(maxWidth: .infinity, maxHeight: .infinity)
                           // .background(Color.pink)
                        
                    }
                   
                    .onMove(perform: moveRow)
                   
//                  .onMove(perform: { indices, toOffset in
//                        fuits.move(fromOffsets: indices, toOffset: toOffset)
//
//                    })
                    .onDelete { IndexSet in
                        delete(IndexSet: IndexSet)
                    }
                }
                Section(header: Text("Veggies")){
                    ForEach(veggie, id: \.self) {i in
                        Text(i)
                    }
                    
                }
                .listRowBackground(Color.pink)
                .padding(.vertical)
            }
            
            .listStyle(
                //SidebarListStyle()
                //PlainListStyle()
                //InsetGroupedListStyle()
                DefaultListStyle()
               // GroupedListStyle()
            )
            .navigationTitle("Grocery List")
            .navigationBarItems(leading: EditButton(),
                                trailing:
                                    Button("Add"){
                                    fuits.append("Coconut")
            })
        }
    }
    
    
    func delete(IndexSet: IndexSet) {
        fuits.remove(atOffsets: IndexSet)
    }
    
    func moveRow(indices: IndexSet, toOffset: Int) {
        fuits.move(fromOffsets: indices, toOffset: toOffset)

    }
}

struct ListViews_Previews: PreviewProvider {
    static var previews: some View {
        ListViews()
    }
}
}
```



[Youtube Tutorial](https://www.youtube.com/watch?v=tkOnXG-sNks&t=0s)

