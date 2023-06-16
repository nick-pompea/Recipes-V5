
# Catche

Example
Modifiers
```swift

import SwiftUI
//MARK: Logic ---------------------------------------
class CatcheTwentyTwoViewModel: ObservableObject {
    
    @Published var startingImage: UIImage? = nil
    let imageName: String = "Steve_Jobs"

    
    init() {
        
    getImageFromAssets()
    }
    
    func getImageFromAssets() {
        startingImage = UIImage(named: imageName)
        
    }
    
//    func remove(name: String) {
//        imageCatche.removeObject(forKey: name as NSString)
//        print("removed")
//    }
//
//
//    func get(name: String) -> UIImage? {
//        return imageCatche.object(forKey: name as NSString)
//    }
//
//    func saveToCatch() {
//        guard let image = startingImage else { return }
//        manager.add(image: image, name: )
//    }
}

class catcheManager {
    
    static let instance = catcheManager()
    private init() { }
    
    var imageCatche: NSCache<NSString, UIImage> = {
        let catche = NSCache<NSString, UIImage>()
        catche.countLimit = 100
        catche.totalCostLimit = 1024 * 1024 * 100 // 100 mb
        return catche
    }()
    
    func add(image: UIImage, name: String) {
        imageCatche.setObject(image, forKey: name as NSString)
        print("Added to catch")
    }
    
 

}

//MARK: View ---------------------------------------
struct Save_and_cache_images: View {
    @StateObject var vm = CatcheTwentyTwoViewModel()
    let manager = catcheManager.instance
    
    var body: some View {
        NavigationView {
            VStack{
                if let image = vm.startingImage {
                    Image(uiImage: image)
                        .resizable()
                        .scaledToFit()
                        .frame(width: 200, height: 200)
                        .clipped()
                        .cornerRadius(10)
                }
                
                
                HStack {
                    Button {
                        
                    } label: {
                        Text("Save to Cache")
                            .font(.headline)
                            .foregroundColor(Color.white)
                            .padding()
                            .background(Color.blue)
                            .cornerRadius(10)
                }
                }
                
                HStack {
                    
                    
                    Button {
                        
                    } label: {
                        Text("Delete to Cache")
                            .font(.headline)
                            .foregroundColor(Color.white)
                            .padding()
                            .background(Color.red)
                            .cornerRadius(10)
                }
                }

                
                Spacer()
                
                
            }
            .navigationTitle("Cache")
        }
        
    }
}





struct Save_and_cache_images_Previews: PreviewProvider {
    static var previews: some View {
        Save_and_cache_images()
    }
 
}


```
[Youtube Tutorial](https://www.youtube.com/watch?v=yXSC6jTkLP4&t=0s)
