<h1>HW2<h1>

```swift

import SwiftUI

struct ContentView: View {
    @State var count:Int=0
    @State var countDown = 3
    @State var iscounting = 1
    @State var randomImageIndex: Int?
    var body: some View {
        ZStack
        {
            if iscounting==0{
                Text("\(countDown)")
                    .font(.system(size:100))
                    .foregroundColor(.gray)
                    .onAppear {
                        let timer = Timer.scheduledTimer(withTimeInterval: 1, repeats: true) { timer in
                            if self.countDown > 1 {
                                self.countDown -= 1
                            } else {
                                iscounting=2
                                countDown=3
                                timer.invalidate()
                                self.randomImageIndex = Int.random(in: 0...2)
                            }
                        }
                        RunLoop.current.add(timer, forMode: .common)
                    }
            }
            else if iscounting==1{
                Button(action: {
                    iscounting = 0
                }, label: {
                    Text("Go")
                        .font(.system(size:30))
                        .frame(width: 150, height: 60, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                        .background(Color.black)
                        .foregroundColor(.gray)
                        .border(/*@START_MENU_TOKEN@*/Color.black/*@END_MENU_TOKEN@*/, width: /*@START_MENU_TOKEN@*/1/*@END_MENU_TOKEN@*/)
                        .cornerRadius(30)
                        .position(x:200,y:500)
                    
                })
            }
            else if iscounting==2{
                Button(action: {
                    iscounting = 0
                }, label: {
                    if let randomImageIndex = self.randomImageIndex {
                        if randomImageIndex == 0 {
                            Image("A")
                                .resizable()
                                .font(.system(size: 0.1))
                                .frame(width: 200, height: 200, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                                .position(x:200, y: 300)
                        } else if randomImageIndex == 1 {
                            Image("B")
                                .resizable()
                                .frame(width: 200, height: 200, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                                .font(.system(size: 0.1))
                                .position(x:200, y: 300)
                        } else if randomImageIndex == 2 {
                            Image("C")
                                .resizable()
                                .frame(width: 200, height: 200, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                                .font(.system(size: 0.1))
                                .position(x:200, y: 300)
                        }
                    }
                    
                })
               
            }
        }
    }
}




```

<img src="https://raw.githubusercontent.com/yzudanny/yzu-Swiftui/main/HitPawOnline_182923.gif">


