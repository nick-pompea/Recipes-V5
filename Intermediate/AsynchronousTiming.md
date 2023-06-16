
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

---
## Fetch

Example
```swift
import SwiftUI

class TaskBootCampViewModel: ObservableObject {
    
    @Published var image: UIImage? = nil
    @Published var image2: UIImage? = nil

    func fetchImage() async {
        do {
            guard let url = URL(string: "https://picsum.photos/1000") else { return }
            let (data, _) = try await URLSession.shared.data(from: url, delegate: nil)
            await MainActor.run(body: {
            self.image = UIImage(data: data)
            })
        } catch { print(error.localizedDescription) }}
    
    func fetchImageTwo() async {
        try? await Task.sleep(nanoseconds: 5_000_000_000)
        do {
            guard let url = URL(string: "https://picsum.photos/1000") else { return }
            let (data, _) = try await URLSession.shared.data(from: url, delegate: nil)
            await MainActor.run(body: {
                self.image2 = UIImage(data: data)
            })
        } catch { print(error.localizedDescription) }}
    
}

struct UsingTask: View {
    
    @StateObject private var viewModel = TaskBootCampViewModel()
    @State private var fetchImageTask: Task<(), Never>? = nil
    
    
    
    var body: some View {
        VStack(spacing: 40) {
            if let image = viewModel.image {
                Image(uiImage: image)
                    .resizable()
                    .scaledToFit()
                    .frame(width: 200, height: 200)
            }
            
            if let image = viewModel.image2 {
                Image(uiImage: image)
                    .resizable()
                    .scaledToFit()
                    .frame(width: 200, height: 200)
            }
        }
        .onDisappear {
            fetchImageTask?.cancel()
        }
        
        .task {
            await viewModel.fetchImageTwo()
        }
        .onAppear(){
            fetchImageTask = Task{
                await viewModel.fetchImage()
            }
            Task{
                await viewModel.fetchImageTwo()
            }
            
            
            Task(priority: .high) {  // .high, .medium, .low
                // try? await Task.sleep(nanoseconds: 2_000_000_000)
                await Task.yield()
                 print ("high : \(Thread.current) : \(Task.currentPriority)")
                
            }
            
            
           
            Task(priority: .userInitiated) {  // .high, .medium, .low
                 print ("userInitiated : \(Thread.current) : \(Task.currentPriority)")
                Task {
                    print ("userInitiated : \(Thread.current) : \(Task.currentPriority)")
                }
            }
            
            
            
        }
    }
}

struct UsingTask_Previews: PreviewProvider {
    static var previews: some View {
        UsingTask()
    }
}
  ```
    
[Youtube Tutorial](https://www.youtube.com/watch?v=fTtaEYo14jI&t=0s)


