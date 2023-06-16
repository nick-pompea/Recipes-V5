
# Arrays

## Adding fixed number elements
```swift
let array = [1,2,3,4,5]
let array2 = Array(items)

```
---
## Array syntax

```swift
let model = Model()
let array = [Model](repeating: model, count: 50)

```
---
## Sort
```swift
func arrayEdit(){
//
array = dataArray.sorted { user1, user2 in
 return user1.points > user2.points }
 }
 ```
Shorthand
```swift
filteredArray = dataArray.sorted(by: { $0.points > $1.points })
```
---
## Filter
```swift
func arrayEdit(){
//
filteredArray = dataArray.filter({ (user) -> Bool  in
return user.points > 50
return user.name.contains("i")
 }
```
Shorthand
```swift
filteredArray = dataArray.filter( { $0.isVerified } )
```
---
## Map
```swift
func arrayEdit(){
//
mappedArray = dataArray.map({ (user) -> String in
return user.name
  })
 }
```
Shorthand
```swift
 mappedArray = dataArray.map({ String($0.points) })
 ```

[Youtube Tutorial](https://www.youtube.com/watch?v=F-gUZztPTgI&t=0s)


---

