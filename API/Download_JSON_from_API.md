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

* Example Combine Model
```swift
import Combine

* [Youtube Tutorial](https://www.youtube.com/watch?v=fdxFp5vU6MQ&t=0s)

//
class DownloadWithCombineViewModel: ObservableObject {
    
    @Published var posts: [PostModelAPICombine] = []
    var cancelable = Set<AnyCancellable>()
    
    init() {
        getPosts()
    }
    
    func getPosts() {
        
        guard let url = URL(string: "https://jsonplaceholder.typicode.com/posts") else { return }
        
        URLSession.shared.dataTaskPublisher(for: url)
           // .subscribe(on: DispatchQueue.global(qos: .background))
            .receive(on: DispatchQueue.main)
            .tryMap(handleOutput)
            .decode(type: [PostModelAPICombine].self, decoder: JSONDecoder())
            .sink { (completion) in
                switch completion {
                case.finished:
                    print ("Finished")
                case.failure(let error):
                    print("error \(error)")
                }
                print("completion \(completion)")
            } receiveValue: { [weak self] (returnedPosts) in
                self?.posts = returnedPosts
            }
            .store(in: &cancelable)
    }
    
    func handleOutput(output: URLSession.DataTaskPublisher.Output) throws -> Data {
        guard
            let response = output.response as? HTTPURLResponse,
            response.statusCode >= 200 && response.statusCode < 300 else {
            throw URLError(.badServerResponse)
        }
        return output.data
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


