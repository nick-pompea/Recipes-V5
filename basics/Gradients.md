```swift
RoundedRectangle(cornerRadius: 25)
                .fill(
                    LinearGradient(
                        gradient: Gradient(
                        colors: [Color(#colorLiteral(red: 0.5921568627, green: 0.1529411765, blue: 0.1254901961, alpha: 1)), Color(#colorLiteral(red: 0.862745098, green: 0.231372549, blue: 0.137254902, alpha: 1))]),
                        startPoint: .leading,
                        endPoint: .trailing)
                )
                .frame(width: 300, height: 200)
            
            RoundedRectangle(cornerRadius: 25)
                .fill(
                    RadialGradient(
                        colors: [Color(#colorLiteral(red: 0.1994512975, green: 0.4021728039, blue: 0.5376263261, alpha: 1)), Color(#colorLiteral(red: 0.4745098054, green: 0.8392156959, blue: 0.9764705896, alpha: 1))],
                        center: .topLeading,
                        startRadius: 5,
                        endRadius: 400)
                )
                .frame(width: 300, height: 200)
            
            AngularGradient(
                gradient: Gradient(
                colors: [Color(#colorLiteral(red: 0.5921568627, green: 0.1529411765, blue: 0.1254901961, alpha: 1)), Color(#colorLiteral(red: 0.862745098, green: 0.231372549, blue: 0.137254902, alpha: 1))]),
                center: .center,
                angle: .degrees(90)
            )
            .frame(width: 300, height: 200)

            AngularGradient(
                gradient: Gradient(
                colors: [Color(#colorLiteral(red: 0.5921568627, green: 0.1529411765, blue: 0.1254901961, alpha: 1)), Color(#colorLiteral(red: 0.862745098, green: 0.231372549, blue: 0.137254902, alpha: 1))]),
                center: .topLeading,
                angle: .degrees(180+45)
            )
            .frame(width: 300, height: 200)
```




[Youtube Tutorial]((https://www.youtube.com/watch?v=EPoxQHwVnj0)
