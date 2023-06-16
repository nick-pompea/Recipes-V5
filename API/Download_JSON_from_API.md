# Download JSON from API

* Example struct
* Tool that automatically creates structured based on JSON response
    * https://app.quicktype.io
```swift
struct PostModelAPI: Identifiable, Codable {
    let userId, id: Int
    let title, body: String
}
```

* Example Model
```swift
class DownloadWithEscapingViewModel: ObservableObject {
    
    // From struct, where data will be saved
    @Published var posts: [PostModelAPI] = []
    
    // Standard init
    init() {
        getPosts()
    }
    
    // getting data from API request url with error handling
    func getPosts() {
        
        guard let url = URL(string: "https://jsonplaceholder.typicode.com/posts") else { return }
        
        downloadData(url: url) { returnedData in
            if let data = returnedData {
                guard let newPosts = try? JSONDecoder().decode([PostModelAPI].self, from: data) else { return }
                DispatchQueue.main.async { [weak self] in
                    self?.posts = newPosts
                }
            } else {
                print("no data")
            }
        }
    }
    
    // Downloading data and checking if URL returns error
    func downloadData(url: URL, completionHandler: @escaping (_ data: Data?) -> ()) {
        URLSession.shared.dataTask(with: url) { (data, response, error) in
            
            guard
                 error == nil,
                let response = response as? HTTPURLResponse,
                 response.statusCode >= 200 && response.statusCode < 300 else {
                print("error with data")
                completionHandler(nil)
                return
            }
            completionHandler(data)
            
        }.resume()
    }
}
```
* View Example
```swift
struct Download_JSON_from_API: View {
    
    @StateObject var vm = DownloadWithEscapingViewModel()
    
    var body: some View {
        
        List{
            ForEach(vm.posts) { i in
                VStack(alignment: .leading) {
                    Text(i.title)
                        .font(.headline)
                    Text(i.body)
                        .foregroundColor(Color.gray)
                }
                .frame(maxWidth: .infinity, alignment: .leading)
            }
        }
    }
}
```
[Youtube Tutorial](https://www.youtube.com/watch?v=h42OHc5CRBQ&t=0s)


