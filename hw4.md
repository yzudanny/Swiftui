
<h1>hw1</h1>

```swift

    
import SwiftUI

struct TermAndDescription: Identifiable{
    var id = UUID()
    var term:String
    var description:String
}

var myDictionary = [
    TermAndDescription(term: "1", description: "1"),
    TermAndDescription(term: "2", description: "2"),
    TermAndDescription(term: "3", description: "3"),
    TermAndDescription(term: "4", description: "4")
]

struct CardView: View{
    @State var currentCard = 0
    var body: some View{
        VStack{
            VStack{
                Text(myDictionary[currentCard].term)
                    .font(.title)
                    .padding(.all,10)
                Text(myDictionary[currentCard].description)
                    .font(.body)
                    .foregroundColor(.blue)
                    .padding(.all,10)
            }.frame(minWidth: 0, idealWidth: 100, maxWidth: 300,
                    minHeight: 0, idealHeight: 100, maxHeight: 300, alignment: .center)
            .background(Color.yellow)
            .onTapGesture{
                if currentCard<myDictionary.count-1{
                    currentCard += 1
                }else{
                    currentCard = 0
                }
            }
            Text("next")
                .padding(.all,10)
        }
    }
}
import SwiftUI

struct ContentView: View { 
    var body: some View {
    VStack{ Text("行動開發學院")
            .font(.largeTitle)
            .fontWeight(.heavy)
            .foregroundStyle(.primary)
        TabView{ 
            Group{
                WelcomeView()
                    .tabItem {
                        Image(systemName: "rosette")
                        Text("Welcome")
                    }
                Text("第一頁")
                    .tabItem {
                        Image(systemName:  "arrowshape.left")
                        Text("Page1")
                    }
                CourseListView()
                    .tabItem {
                        Image(systemName: "list.dash")
                        Text("Courses")
                    }
                Text("第三頁") 
                    .tabItem {
                        Image(systemName: "arrowshape.right")
                        Text("Page3")
                    }
                CardView()
                    .tabItem {
                        Image(systemName: "book")
                        Text("Learn")
                    } 
                SettingView()
                    .tabItem {
                        Image(systemName: "wrench")
                        Text("Setting")
                    }
            }
            .toolbarBackground(Color.black,for:.tabBar)
            .toolbarBackground(.visible,for:.tabBar)
            }
        .tint(.yellow)
        }
    }
}
import SwiftUI

struct Course: Identifiable{
    var id = UUID()
    var name:String
    var image:String
    var description:String
}
var courses=[
    Course(name: "a", image: "A",description:"1"),
    Course(name: "b", image: "B",description:"2"),
    Course(name: "c ", image: "C",description:"3"),
    Course(name: "d", image: "D",description:"4"),
    Course(name: "e", image: "E",description:"5"),
]
struct BasicImageRow: View {
    var thisCourse: Course
    var body: some View {
        HStack{
            Image(thisCourse.image)
                .resizable()
                .frame(width:40,height:40)
                .cornerRadius(5)
            Text(thisCourse.name)
        }
    }
}

struct CourseDetailView: View {
    @Environment(\.presentationMode) var presentationMode
    var thisCourse: Course
    var body: some View {
        ScrollView{
            VStack{
                Image(thisCourse.image)
                    .resizable()
                    .aspectRatio(contentMode: .fill)
                    .clipped()
                Text(thisCourse.name)
                    .font(.system(.title, design: .rounded))
                    .fontWeight(.black)
                Spacer()
                Text(thisCourse.description)
                    .font(.system(.subheadline, design: .rounded))
                    .fontWeight(.light)
                Spacer()
            }
        }.overlay(
            HStack{
                Spacer()
                VStack{
                    Button(action:{
                        self.presentationMode.wrappedValue.dismiss()
                    },label:{
                        Image(systemName:"chevron.down.circle.fill")
                            .font(.largeTitle)
                            .foregroundColor(.white)
                    })
                    .padding(.trailing,20)
                    .padding(.top,40)
                    Spacer()
                }
            }
        )}
}

struct CourseListView: View {
    @State var showDetailView = false
    @State var selectedCourse:Course?
    var body: some View {
        NavigationView{
            List(courses){ citem in
                BasicImageRow(thisCourse: citem)
                    .onTapGesture {
                        self.showDetailView = true
                        self.selectedCourse = citem
                    }
            }.sheet(item: self.$selectedCourse){ thisCourse in
                CourseDetailView(thisCourse: thisCourse)
            }
            .navigationTitle("課程列表")
        }
    }
}
import SwiftUI

struct SettingView: View { 
    
    let displayFontType=[".default",".round",".monospaces","serif"]
    @State var displayFontselected = 0
    @State var IsDeepScheme = false
    @State var colorArray:Array = [255.0,255.0,255.0]
    @State var stepperValue = 0
    @State var sliderValue = 0.0
    @State var selectedDate = Date()
    @AppStorage("UserName") var UserName: String = ""
    var body: some View{
        NavigationView{
            Form(content: {
                Section(content: {
                    TextField("Please enter your name", text: $UserName)
                },header: {
                    Text("UserName")
                })
                Section(header:Text("Font settings"),content:{
                    Picker(selection: $displayFontselected,
                           label: Text("Font choice(\(displayFontselected))"),
                           content:{
                        ForEach(0..<displayFontType.count,
                                id:\.self,
                                content: {
                            Text(self.displayFontType[$0])
                        })
                    })
                })
                Section(header: Text("background style"),
                        content: {
                    Toggle(isOn: $IsDeepScheme,
                           label: {Text("dark(\(String(IsDeepScheme))")
                    })
                })
                Section(header: Text("Stepper")){
                    Stepper("Stepper(\(stepperValue))",
                            onIncrement:{stepperValue+=1},
                            onDecrement:{stepperValue-=1})
                }
                Section(header: Text("Slider(\(sliderValue,specifier:"%.2f"))")){
                    Slider(value:$sliderValue,in:0...1)
                }
                Section(header: Text("Date Picker")) {
                    DatePicker("Selected Date", selection: $selectedDate, displayedComponents: .date)
                        .datePickerStyle(GraphicalDatePickerStyle())
                        .onChange(of: selectedDate) { newValue in
                            print("Selected Date: \(newValue)")
                        }
                }
            })
            .navigationBarTitle("Settings")
        }
    }
}


import SwiftUI

struct WelcomeView: View { 
    @AppStorage("UserName") var Username: String = ""
    var body: some View {
        VStack{
            Text(Username.isEmpty ? "" : Username)
                .font(.system(size: 30))
            Image("Mobiledevtw")
                .resizable()
                .frame(width: 150, height: 150)
                .aspectRatio(contentMode: .fit) 
            Text("資訊技術培訓\nWeb/APP/AI應用開發")
                .fontWeight(.heavy)
                .lineSpacing(20)
                .font(.system(size: 32.0))
                .foregroundColor(.white)
                .frame(width: 350, height: 150, alignment: .center)
                .background(Color.blue)
                .cornerRadius(20.0)
                .multilineTextAlignment(.center)
            
        }
    } 
}






```

<img src="https://raw.githubusercontent.com/yzudanny/yzu-Swiftui/main/IMG_0274.jpeg">
