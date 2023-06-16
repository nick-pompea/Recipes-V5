# Publishers and Subscribers

Example
```swift

import SwiftUI
import Combine

class SubscriberViewModel: ObservableObject {
    @Published var count: Int = 0
    var cancellables = Set<AnyCancellable>()
    @Published var textFieldText: String = ""
    @Published var textIsValid: Bool = false
    @Published var showButton: Bool = false


    init() {
        setUpTimer()
        addTextFieldSubscriber()
        addButtonSubscriber()
    }
    
    func addTextFieldSubscriber() {
        $textFieldText
           // .debounce(for: .seconds(0.2), scheduler: DispatchQueue.main)
            .map { (text) -> Bool in
                if text.count > 3 {
                    return true
                }
                return false
            }
       //     .assign(to: \.textIsValid, on: self)
            .sink(receiveValue: { [weak self] (isValid) in
                self?.textIsValid = isValid
            })
            .store(in: &cancellables)
    }
    
    func setUpTimer() {
    Timer
            .publish(every: 1, on: .main, in: .common)
            .autoconnect()
            .sink { [weak self] _ in
                guard let self = self else { return }
                self.count += 1
            }
            .store(in: &cancellables)
    }
    
    func addButtonSubscriber() {
        $textIsValid
            .combineLatest($count)
            .sink { [weak self] (isValid, count) in
                guard let self = self else { return }
                if isValid && count >= 10 {
                    self.showButton = true
                } else {
                    self.showButton = false
                }
            }
            .store(in: &cancellables)

    }

}

struct Publishers_and_Subscribers: View {
    
    @StateObject var vm = SubscriberViewModel()
    let colorMercury: Color = Color(#colorLiteral(red: 0.921431005, green: 0.9214526415, blue: 0.9214410186, alpha: 1))
    
    var body: some View {
        VStack{
            Text("\(vm.count)")
                .font(.largeTitle)
            
            
            TextField("Type here ...", text: $vm.textFieldText)
                .padding(.leading)
                .frame(height: 55)
                .font(.headline)
                .background(colorMercury)
                .cornerRadius(10)
                .overlay(
                    ZStack{
                        
                        Image(systemName: "xmark")
                            .foregroundColor(Color.red)
                            .opacity(
                                vm.textFieldText.count < 1 ? 0.0 :
                                
                                vm.textIsValid ? 0.0 : 1.0)
                        Image(systemName: "checkmark")
                            .foregroundColor(Color.green)
                            .opacity(vm.textIsValid ? 1.0 : 0.0)

                    }
                
                .font(.title)
                .padding(.trailing)
            , alignment: .trailing
                    )
            
            Button {
                
            } label: {
                Text("Submit".uppercased())
                    .font(.headline)
                    .foregroundColor(Color.white)
                    .frame(height: 55)
                    .frame(maxWidth: .infinity)
                    .background(Color.blue)
                    .cornerRadius(10)
                    .opacity(vm.showButton ? 1.0 : 0.5)
                
            }
            .disabled(!vm.showButton)

        }
        .padding()
    }
}

struct Publishers_and_Subscribers_Previews: PreviewProvider {
    static var previews: some View {
        Publishers_and_Subscribers()
    }
}


```
[Youtube Tutorial](https://www.youtube.com/watch?v=Q-1EDHXUunI&t=0s)

