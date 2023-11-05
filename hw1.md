<h1>hw1<h1>

```swift

import SwiftUI

struct ContentView: View {
    var body: some View {
        ZStack{
            Image("qwe")
                .resizable()
                .aspectRatio(contentMode: .fill)
                .opacity(0.7)
                .frame(width: 500, height:100, alignment: .center)
            Text("劉承軒")
                .font(.title)
                .frame(width: 150, height: 70, alignment: .center)
                .background(Color.primary)
                .cornerRadius(40)
                .position(x: 365, y: 340)
                .foregroundStyle(LinearGradient(
                    colors: [.red,.blue,.green],
                    startPoint: .leading,
                    endPoint:.trailing
                ))
                .opacity(0.48)
                .bold()            
            Text("1103315")
                .font(.title)
                .frame(width: 150, height: 70, alignment: .center)
                .background(Color.primary)
                .cornerRadius(40)
                .position(x: 365, y: 420)
                .foregroundStyle(LinearGradient(
                    colors: [.red,.blue,.green],
                    startPoint: .leading,
                    endPoint:.trailing
                ))
                .opacity(0.48)
                .bold()        
            
            Text("籃球")
                .font(.title)
                .frame(width: 150, height: 70, alignment: .center)
                .background(Color.primary)
                .cornerRadius(40)
                .position(x: 365, y: 500)
                .foregroundStyle(LinearGradient(
                    colors: [.red,.blue],
                    startPoint: .leading,
                    endPoint:.trailing
                ))
                .opacity(0.48)
                .bold()          
            Image(systemName: "figure.basketball")
                .foregroundStyle(LinearGradient(
                    colors: [.blue,.green],
                    startPoint: .leading,
                    endPoint:.trailing
                ))
                .font(.system(size: 40))
                .position(x:415, y: 500)    
                .opacity(0.48)
        }
        .overlay(
            Text("面對陽光你就不會看到陰影")
                .font(.system(size:20))
                .bold()
                .frame(width: 300, height: 50, alignment: .center)
                .foregroundStyle(LinearGradient(
                    colors: [.red,.blue,.green],
                    startPoint: .leading,
                    endPoint:.trailing
                ))
                .background(Color.primary)
                .opacity(0.58)
                .cornerRadius(40)
            ,
            alignment: .bottom
        )
    }
}



```
<img src="https://raw.githubusercontent.com/yzudanny/Swiftui/new/main/IＭG_0249.jpeg">
