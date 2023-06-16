# Playing Sounds

* Sound Manager
```swift
class soundManager {
    
    static let instance = soundManager()
    
    var player: AVAudioPlayer?
    
    enum soundOption: String {
        case One
        case Three
    }
    
    func playSound(sound: soundOption) {
        guard
            let url = Bundle.main.url(forResource: sound.rawValue, withExtension: ".mp3")
        else { return }
        
        do {
            player = try AVAudioPlayer(contentsOf: url)
            player?.play()
        } catch let error {
            print("Error playing sound. \(error.localizedDescription)")
        }
        
    }
}
```
* Access sound manager 
```swift
           Button {
                soundManager.instance.playSound(sound: .One)
            } label: {
                Text("Play Sound 1")
            }
```
* Add sound to XCode Assets 



[Youtube Tutorial](https://www.youtube.com/watch?v=iBLZ1C4L5Mw&t=0s)

