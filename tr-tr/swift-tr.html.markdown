---
language: swift
contributors:
  - ["Grant Timmerman", "http://github.com/grant"]
translators:
    - ["Haydar KULEKCI", "http://scanf.info/"]
lang: tr-tr
filename: learnswift.swift
---

Swift programlama dili Apple tarafından iOS ve OS X geliştirmeleri yapmak içindir.
Objective-C ile bir arada olması için ve hatalı kodlara karşı daha dayanıklı
olması için tasarlandı, Swift 2014 WWDC konferansında tanıtıldı. Xcode 6 Beta
içerisindeki LLVM derleyicisi ile kurulur.

Apple'ın [Başlangıç Rehberi](https://developer.apple.com/library/prerelease/ios/referencelibrary/GettingStarted/LandingPage/index.html)'ne göz atabilirsiniz.


```js
//
// Temeller
//

println("Merhaba, dünya")
var myVariable = 42  // Normal bir değişken
let myConstant = 3.1415926  // Sabit Değer
let explicitDouble: Double = 70  // Double veri tipinde bir değişken
let label = "some text " + String(myVariable)     // Cast Etmek
let piText = "Pi = \(myConstant)"                 // String interpolation
var optionalString: String? = "optional"          // nil değerinde olabilir
optionalString = nil


//
// Dİziler ve Sözlükler
//

// Dizi
var shoppingList = ["catfish", "water", "lemons"]
shoppingList[1] = "bottle of water"
let emptyArray = String[]()

// Sözlük
var occupations = [
  "Malcolm": "Captain",
  "kaylee": "Mechanic"
]
occupations["Jayne"] = "Public Relations"
let emptyDictionary = Dictionary<String, Float>()


//
// Kontrol Yapıları
//

// for döngüsü (dizi ile)
let myArray = [1, 1, 2, 3, 5]
for value in myArray {
  if value == 1 {
    println("Bir!")
  } else {
    println("Bir değil!")
  }
}

// for döngüsü (sözlük ile)
for (key, value) in dict {
  println("\(key): \(value)")
}

// for Döngüsü (range ile)
for i in -1...1 { // [-1, 0, 1]
  println(i)
}
// son numarayı almamak için .. kullanın

// while döngüsü
var i = 1
while i < 1000 {
  i *= 2
}

// do-while döngüsü
do {
  println("merhaba")
} while 1 == 2

// Switch yapısı
let vegetable = "kırmızı biber"
switch vegetable {
case "celery":
  let vegetableComment = "Add some raisins and make ants on a log."
case "cucumber", "watercress":
  let vegetableComment = "That would make a good tea sandwich."
case let x where x.hasSuffix("pepper"):
  let vegetableComment = "Is it a spicy \(x)?"
default: // required (in order to cover all possible input)
  let vegetableComment = "Everything tastes good in soup."
}


//
// Fonksiyonlar
//

// Fonksiyonlar first-class tipdir, bunun anlamı bir fonksiyon içerisinde
// olabilirler.

// Fonksiyon
func greet(name: String, day: String) -> String {
  return "Hello \(name), today is \(day)."
}
greet("Bob", "Tuesday")

// Tuple içerisinde birden fazla değer dönen bir fonksiyon
func getGasPrices() -> (Double, Double, Double) {
  return (3.59, 3.69, 3.79)
}

// Args
func setup(numbers: Int...) {}

// Fonksiyon gönderme ve döndürme
func makeIncrementer() -> (Int -> Int) {
  func addOne(number: Int) -> Int {
    return 1 + number
  }
  return addOne
}
var increment = makeIncrementer()
increment(7)


//
// Closure'lar
//

// Functions are special case closures ({})

// Closure örneği.
// `->` separates the arguments and return type
// `in` separates the closure header from the closure body
numbers.map({
  (number: Int) -> Int in
  let result = 3 * number
  return result
  })

// When the type is known, like above, we can do this
var numbers = [1, 2, 6]
numbers = numbers.map({ number in 3 * number })
print(numbers) // [3, 6, 18]


//
// Sınıflar
//

// Bir sınıfın tüm metodları ve özellikleri public'dir.
// Eğer bir yapı içerisinde verilerinizi barındırmak istiyorsanız
// `struct` kullanabilirsiniz.

// Basit bir `Square` sınıfı `Shape` sınıfından türer
class Rect: Shape {
  var sideLength: Int = 1

  // Custom getter and setter property
  var perimeter: Int {
    get {
      return 4 * sideLength
    }
    set {
      sideLength = newValue / 4
    }
  }

  init(sideLength: Int) {
    super.init()
    self.sideLength = sideLength
  }

  func shrink() {
    if sideLength > 0 {
      --sideLength
    }
  }

  override func getArea() -> Int {
    return sideLength * sideLength
  }
}
var mySquare = new Square(sideLength: 5)
print(mySquare.getArea()) // 25
mySquare.shrink()
print(mySquare.sideLength) // 4

// If you don't need a custom getter and setter,
// but still want to run code before and after getting or setting
// a property, you can use `willSet` and `didSet`


//
// Enums
//

// Enums can optionally be of a specific type or on their own.
// They can contain methods like classes.

enum Suit {
  case Spades, Hearts, Diamonds, Clubs
  func getIcon() -> String {
    switch self {
    case .Spades: return "♤"
    case .Hearts: return "♡"
    case .Diamonds: return "♢"
    case .Clubs: return "♧"
    }
  }
}


//
// Other
//

// `protocol`: Similar to Java interfaces.
// `extension`s: Add extra functionality to an already created type
// Generics: Similar to Java. Use the `where` keyword to specify the
//   requirements of the generics.

```