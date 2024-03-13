```
import Foundation

// Copy on Write (CoW) и структура IOSCollection
struct VideoLesson {
    let title: String
    let duration: Int
}

struct IOSCollection {
    private var videos: [VideoLesson]
    
    init(videos: [VideoLesson] = []) {
        self.videos = videos
    }
    
    mutating func addVideo(_ video: VideoLesson) {
        videos.append(video)
    }
}

// Протокол Hotel и класс HotelAlfa
protocol Hotel {
    init(roomCount: Int)
}

class HotelAlfa: Hotel {
    var roomCount: Int
    
    required init(roomCount: Int) {
        self.roomCount = roomCount
    }
}

// Протокол GameDice и расширение Int
protocol GameDice {
    var numberDice: Int { get }
}

extension Int: GameDice {
    var numberDice: Int {
        return self
    }
}

let diceCoub = 4
print("Выпало \(diceCoub.numberDice) на кубике")

// Протокол с методом и свойствами, подписанный класс
protocol SomeProtocol {
    var property1: Int { get }
    var property2: String? { get set }
    
    func someMethod()
}

class SomeClass: SomeProtocol {
    var property1: Int
    var property2: String?
    
    init(property1: Int) {
        self.property1 = property1
    }
    
    func someMethod() {
        print("Implemented method in SomeClass")
    }
}

// Протоколы Делегирование
protocol Development {
    var time: Int { get }
    var codeCount: Int { get }
    
    func writeCode(platform: Platform, numberOfSpecialist: Int)
}

protocol Coding {
    func stopCoding()
}

class Company: Development, Coding {
    var time: Int
    var codeCount: Int
    var numberOfProgrammers: Int
    var specializations: [String]
    
    init(time: Int, codeCount: Int, numberOfProgrammers: Int, specializations: [String]) {
        self.time = time
        self.codeCount = codeCount
        self.numberOfProgrammers = numberOfProgrammers
        self.specializations = specializations
    }
    
    func writeCode(platform: Platform, numberOfSpecialist: Int) {
        // Начинаем разработку
        print("Разработка началась. Пишем код для \(platform) специалистами в количестве \(numberOfSpecialist)")
    }
    
    func stopCoding() {
        // Заканчиваем разработку
        print("Работа закончена. Сдаю в тестирование")
    }
}

enum Platform {
    case iOS, Android, Web
}

// Пример использования
let company = Company(time: 100, codeCount: 500, numberOfProgrammers: 10, specializations: ["iOS", "Android", "Web"])
company.writeCode(platform: .iOS, numberOfSpecialist: 5)
company.stopCoding()

```

![изображение](https://github.com/vihuhool/swifty5/assets/69204363/616650c5-a701-4eab-b985-79449af1071a)
