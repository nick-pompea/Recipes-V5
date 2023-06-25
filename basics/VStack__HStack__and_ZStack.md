
# Stacks

ZStack
* 3d
* Background
* Can set order with .zIndex(4)

```swift
 ZStack(alignment: .top){
 <#code#>
 }
```

HStack
* 2d
* Horizontal

```swift
 HStack{
                
}

HStack(alignment: .bottom, spacing: 10) {
<#code#>
}
```

VStack
* 2d
* Vertical

```swift
 VStack{
<#code#>         
}

VStack(alignment: .center, spacing:  8, content: {
<#code#>
}
```


# Center items
```swift
                    .frame(maxWidth: .infinity, maxHeight: .infinity, alignment: .leading)
```
