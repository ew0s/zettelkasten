# Конструкция If и опциональные типы в Swift

[[Swift]]

В этой статье будет объяснено устройство условных конструкций в swift

---

#### if

```swift
if condition {
    ...
}
```

```swift
if condition {
    ...
} else {
    ...
}
```

```swift
if condition {
    ...
} else if conditionTwo {
    ...
} else {
    ...
}
```

---

#### Тернарный оператор

> Альтернатива if condition {...} else {...}

```swift
let a = 5

a < 10 ? print("True") : print("False") 
```

---

#### Switch statement

```swift
switch значение для сопоставления {
case value 1:
    ...
case value 2:
    ...
default:
    ...
}
```

```swift
switch значение для сопоставления {
case value 1, value 2:
    ...
case value 3:
    ...
default:
    ...
}
```

---

#### Соответствие диапазону

```swift
let aproximateCount = 62

switch aproximateCount {
case ..<0:
    print("Error")
case 0:
    print("Zero")
case 1:
    print("One")
case 2..<5:
    print("2..4")
case 5...11:
    print("5...11")
default
    print("12...")
}
```

---

#### Опциональные типы

```swift
let someString = "" // empty
let someStringTwo: String // 
var optionalString: String? // nil

let possibleNumber = "123"
var convertedNumber = Int(possibleNumber) // 123: Int?

let possibleNumber2 = "123r"
var convertedNumber2 = Int(possibleNumber) // nil: Int?
```

> Данные опционального типа используются там, где заведомо неизвестно, что будет находится в переменной. Например для изображений, полей с местоположением и т.д. 

---

#### Извлечение опциональных типов

Запись вида:

```swift
let possibleNumber = "123"
let convertedNumber = Int(possibleNumber)
print(convertedNumber)
```
выведет на консоль ```Optional(123)```. Таким образом, просто обратившись к опциональному типу, мы не можем получить его значение.

##### Принудительное извлечение опционала

> Оператор ! (unwrap operator) используется для принудительного извлечения опционала

```swift
let possibleNumber = "123f"
let convertedNumber = Int(possibleNumber)

if (convertedNumber == nil) {
    print("convertedNumber does not contains integer value")
}

if (convertedNumber != nil) {
    print("convertedNumber is an integer value and = \(convertedNumber!)")
}
```

Нежелательно использовать этот метод, потому что так мы можем выстрелить себе в ногу. 

> Оператор ?? (оператор nil объединения) может использоваться для извлечения значения опционального типа

```swift
if (convertedNumber != nil) {
    print("convertedNumber is an integer value and = \(convertedNumber ?? 0)")
}
```

В этом примере, если convertedNumber не получится извлечь, будет взято значение 0.

##### Привязка опционалов

```swift
if let number = convertedNumber {
    print(number)
}

if let convertedNumber = convertedNumber {
    print(number)
} else {
    print("Error!!!")
}
```

* В данном примере условие ```let number = convertedNumber``` выполнится только тогда, когда получится успешно создать переменную __number__. А переменную __number__ получится создать только в случае, если __convertedNumber__ не будет равен __nil__.
* Переменная number будет существовать только внутри блока этого __if__
* Рекомендуется называть __number__ тем же именем что и опциональный тип, который мы извлекаем.

##### Неявное извлечение опционала

```swift
var name = ""
var userName: String! = "Tim Cook"
```

После того, как это свойство инициализировалось, мы сможем с ними работать как с обычным типом, как в примере ниже

```swift
let a = 2
var b: Int! = Int("123")
let c = a + b

print(c)
```