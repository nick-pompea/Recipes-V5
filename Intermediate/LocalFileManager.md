
# Local File Manager

Example
```swift

import SwiftUI
//MARK: LocalFileManager ---------------------------------------

class LocalFileManager {
    static let instance = LocalFileManager()
    let folderName = "MyApp_Images"

    init() {
        createFolderIfNeeded()
    }
    
    func createFolderIfNeeded() {
        guard
            let path = FileManager
                .default
                .urls(for: .cachesDirectory, in: .userDomainMask)
                .first?
                .appendingPathComponent("MyApp_Images")
                .path else {
            return
        }
        
        if !FileManager.default.fileExists(atPath: path) {
            do {
                try FileManager.default.createDirectory(atPath: path, withIntermediateDirectories: true, attributes: nil)
                print("success folder")
            } catch let error {
                print("Error with folder \(error)")
            }
        }
    }
    
    func deleteFolder() {
        guard
            let path = FileManager
                .default
                .urls(for: .cachesDirectory, in: .userDomainMask)
                .first?
                .appendingPathComponent("MyApp_Images")
                .path else {
            return
        }
        do {
            try FileManager.default.removeItem(atPath: path)
            print("folder deleted")
        } catch let error {
            print ("error delete \(error)")
        }
    }
    
    
    func saveImage(image: UIImage, name: String) -> String {
        guard let data = image.jpegData(compressionQuality: 1.0),
              let path = getPathForImage(name: name) else {
            return "Error with data"
        }
        do {
          try data.write(to: path)
            print(path)
            return "Successes"
        } catch let error {
            return "error \(error)"
        }
    }
    
    func getImage(name: String) -> UIImage? {
        guard let path = getPathForImage(name: name)?.path,
              FileManager.default.fileExists(atPath: path) else {
            print ("error with path")
            return nil
        }
        return UIImage(contentsOfFile: path)
    }
    
    func deleteImage(name: String) -> String {
        guard
            let path = getPathForImage(name: name),
              FileManager.default.fileExists(atPath: path.path) else {
            return "error with path"
            
        }
        do {
            try FileManager.default.removeItem(at: path)
            return "Success delete"
        } catch let error {
            return "Error \(error)"
        }
    }
    
    func getPathForImage(name: String) -> URL? {
        guard let path = FileManager
            .default
            .urls(for: .cachesDirectory, in: .userDomainMask)
            .first?
            .appendingPathComponent(folderName)
            .appendingPathComponent("\(name).jpg") else {
            print("Error getting path")
            return nil
        }
        return path
    }
}

// MARK: File Manager
class FileManagerViewModle: ObservableObject {
    @Published var image: UIImage? = nil
    let imageName: String = "Steve_Jobs"
    let manager = LocalFileManager.instance
    @Published var infomessage: String = ""
    
    init(){
      //  getImage()
        getImageFromAssetsFolder()
       // getImageFromFileManager()
    }
    
    func getImage() {
        image = UIImage(named: imageName)
    }
    
    func getImageFromFileManager() {
        image = manager.getImage(name: imageName)
    }
    
    func getImageFromAssetsFolder() {
        image = UIImage(named: imageName)
    }
    
    func saveImage() {
        guard let image = image else { return }
       infomessage = manager.saveImage(image: image, name: imageName)
    }
    
    func deleteImage() {
     infomessage = manager.deleteImage(name: imageName)
        manager.deleteFolder()
    }
}

//MARK: View ---------------------------------------
struct FileManagerView: View {
    @StateObject var vm = FileManagerViewModle()
    var body: some View {
        NavigationView {
            VStack{
                
                if let imageOne = vm.image {
                    Image(uiImage: imageOne)
                        .resizable()
                        .scaledToFit()
                        .frame(width: 200, height: 200)
                        .clipped()
                        .cornerRadius(10)
                }
                
                VStack{
                    Button {
                        vm.saveImage()
                    } label: {
                        Text("Save to File Manager")
                            .foregroundColor(Color.white)
                            .font(.headline)
                            .padding()
                            .padding(.horizontal)
    //                        .frame(height: 55)
    //                        .frame(maxWidth: .infinity)
                            .background(Color.blue)
                            .cornerRadius(10)
                    }
                    
                    
                    
                    Button {
                        vm.deleteImage()
                    } label: {
                        Text("Delete from FM")
                            .foregroundColor(Color.white)
                            .font(.headline)
                            .padding()
                            .padding(.horizontal)
                        //                        .frame(height: 55)
                        //                        .frame(maxWidth: .infinity)
                            .background(Color.red)
                            .cornerRadius(10)
                    }
                    Text(vm.infomessage)
                        .font(.largeTitle)
                        .fontWeight(.semibold)
                    
                    Spacer()
                }
            }
            .navigationTitle("File Manager")
        }
    }
}

struct FileManagerView_Previews: PreviewProvider {
    static var previews: some View {
        FileManagerView()
    }

}


```
[Youtube Tutorial](https://www.youtube.com/watch?v=Yiq-hdhLzVM&t=0s)

