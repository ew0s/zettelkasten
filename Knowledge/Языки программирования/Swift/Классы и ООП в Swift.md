# Классы и ООП в Swift

#Swift

В этой статье описаны классы и основы ООП в __Swift__

---

### Классы

```swift
class Human {
    let name: String
    var age = 0

    init() {}
    
    init(name: String) {
        self.name = name
    }
    
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
    
    func walk() {
        print("I can walk")
    }
    
    func sleep() {
        print("I need sleep")
    }
    
    func eat() {
        "I need food"
    }
}
```

Все поля в классе являются его свойствами.
Классы могут иметь методы.

#### Инициализация классов

Для инициализации классов используются инициализаторы, которые по сути являются конструкторами и помечаются ключевым словом ```init(...)```.


---

### Инкапсуляция

Для того, чтобы обеспечивать инкапсуляцию, есть ключевые слова ```public``` и ```private```. Но использовать ```public``` не нужно, так как все свойства и методы в классе по умолчанию публичны. 

---

### Наследование

Для наследования в __swift__ используется оператор __:__

```swift
class Child: Human {
    
    func nursing() {
        if age <= 5 {
            print("I need care")
        } else {
            print("I can eat independently")
        }
    }
    
    func parenting() {
        if age >= 5 && age <= 13 {
            print("I need an education")
        } else if age < 5 {
            print("Me too early to educate")
        } else {
            print("Me too late to educate")
        }
    }   
}
```

---

### Полиморфизм

Для того, чтобы сделать метод переопределяемым в классах наследниках, не нужно использовать ключевое слово __virtual__. Достаточно использовать в методах дочерних классов с таким же названием ключевое слово ```override```. 

```swift
class Shape {
    func draw() {
        print("Drow some shape")
    }
}

class Rectangle: Shape {
    override func draw() {
        print("Drow Rectangle")
    }
}

class Triangle: Shape {
    override func draw() {
        print("Drow Triangle")
    }
}

class Circle: Shape {
    override func draw() {
        print("Drow Circle")
    }
}

let rectangle = Rectangle()
let triangle = Triangle()
let circle = Circle()

drawShape(rectangle)
drawShape(triangle)
drawShape(circle)
```