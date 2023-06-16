
# Asynchronous Timeing 


## Delay
```swift
DispatchQueue.main.asyncAfter(deadline: .now() + 5) {
                
}


```
---

## Multi Threading

Move off than back on main thread
```swift
        DispatchQueue.global(qos: .background).async {
            let newData = self.downloadDate()
            
            print("check 1 \(Thread.isMainThread)")
            print("check 2 \(Thread.current)")
          
            
            DispatchQueue.main.async {
                self.dataArray = newData
                print("check 1 \(Thread.isMainThread)")
                print("check 2 \(Thread.current)")
              
            }
        }


```

Example
```swift

import SwiftUI

class BackgroundThreadViewModel: ObservableObject {
    @Published var dataArray: [String] = []
    
    func fetchData() {
        
        DispatchQueue.global(qos: .background).async {
            let newData = self.downloadDate()
            
            print("check 1 \(Thread.isMainThread)")
            print("check 2 \(Thread.current)")
          
            
            DispatchQueue.main.async {
                self.dataArray = newData
                print("check 1 \(Thread.isMainThread)")
                print("check 2 \(Thread.current)")
              
            }
        }
    }
    
   private func downloadDate() -> [String] {
        var data: [String] = []
        
        for x in 0..<100 {
            data.append("\(x)")
            print(data)
        }
        return data
    }
    
}

struct Multi_threadingView: View {
    
    @StateObject var vm = BackgroundThreadViewModel()
    
    var body: some View {
        ScrollView{
          LazyVStack{
                Text("Load Data")
                    .font(.largeTitle)
                    .fontWeight(.semibold)
                    .onTapGesture {
                        vm.fetchData()
                    }
                
                ForEach(vm.dataArray, id: \.self) { i in
                    Text(i)
                        .font(.headline)
                        .foregroundColor(Color.red)
                }
            }
        }
    }
}

struct Multi_threadingView_Previews: PreviewProvider {
    static var previews: some View {
        Multi_threadingView()
    }
}
[Youtube Tutorial](https://www.youtube.com/watch?v=jEpg2SYvVV8&t=0s)


```
---

## Weak Self

Example
```swift
    func getData() {
        DispatchQueue.main.asyncAfter(deadline: .now() + 500) { [weak self] in
            self?.data = "New data"
        }
    }
  ```
    
[Youtube Tutorial](https://www.youtube.com/watch?v=TPHp9kR0Go8&t=0s)



