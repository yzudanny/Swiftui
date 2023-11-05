<h1>Hw3</h1>

```swift


  import SwiftUI
struct ContentView:View{
    var body:some View{
        
        ZStack{
            Image("Back")
                .resizable()
            VStack(spacing:120){
                HStack(spacing:40){
                    TomatoView()
                    BananaView()
                    GuavaView()
                }
                .padding(.top, 70)
                HStack(spacing:40){
                    pic1View()
                    pic2View()
                    pic3View()
                }
                .padding(.leading, 0)
                HStack(spacing:40){
                    pic4View()
                    pic5View()
                    pic6View()
                }
                .padding(.bottom,-50)
            }
            
        }
    }
}
struct TomatoView: View {
    var body: some View {
        VStack {
            Image("Switch")
                .resizable()
                .aspectRatio( contentMode: .fit)
                .frame(width: UIScreen.screenWidth/12-2,height: UIScreen.screenHeight/12-2,alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
           /* 
           Text("tomato")
                .fontWeight(.bold)
                .font(.system(size: 0))*/
        }
        }
}
struct BananaView:View{
    var body:some View{
        VStack{
            Image("Ps5")
                .resizable()
                .aspectRatio( contentMode: .fit)
                .frame(width: UIScreen.screenWidth/12-2,height: UIScreen.screenHeight/12-2, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        }
    }
}
struct GuavaView:View{
    var body:some View{
        VStack{
            Image("PS4")
                .resizable()
                .aspectRatio( contentMode: .fit)
                .frame(width: UIScreen.screenWidth/12-2,height: UIScreen.screenHeight/12-2, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        }
    }
}
struct pic1View:View{
    var body:some View{
        VStack{
            Image("Pic1")
                .resizable()
                .aspectRatio( contentMode: .fit)
                .frame(width: UIScreen.screenWidth/12-2,height: UIScreen.screenHeight/12-2, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        }
    }
}
struct pic2View:View{
    var body:some View{
        VStack{
            Image("Pic2")
                .resizable()
                .aspectRatio( contentMode: .fit)
                .frame(width: UIScreen.screenWidth/12-2,height: UIScreen.screenHeight/12-2, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        }
    }
}
struct pic3View:View{
    var body:some View{
        VStack{
            Image("Pic3")
                .resizable()
                .aspectRatio( contentMode: .fit)
                .frame(width: UIScreen.screenWidth/12-2,height: UIScreen.screenHeight/12-2, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        }
    }
}
struct pic4View:View{
    var body:some View{
        VStack{
            Image("Pic4")
                .resizable()
                .aspectRatio( contentMode: .fit)
                .frame(width: UIScreen.screenWidth/12-2,height: UIScreen.screenHeight/12-2, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        }
    }
}
struct pic5View:View{
    var body:some View{
        VStack{
            Image("Pic5")
                .resizable()
                .aspectRatio( contentMode: .fit)
                .frame(width: UIScreen.screenWidth/12-2,height: UIScreen.screenHeight/12-2, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        }
    }
}
struct pic6View:View{
    var body:some View{
        VStack{
            Image("Pic6")
                .resizable()
                .aspectRatio( contentMode: .fit)
                .frame(width: UIScreen.screenWidth/12-2,height: UIScreen.screenHeight/12-2, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        }
    }
}
    extension UIScreen{
        static let screenWidth=UIScreen.main.bounds.size.width
        static let screenHeight=UIScreen.main.bounds.size.height
        static let screensize=UIScreen.main.bounds.size
    }
    


```

<img src="https://raw.githubusercontent.com/Jhan711069/Swiftui/main/IMG_0251.jpeg">
