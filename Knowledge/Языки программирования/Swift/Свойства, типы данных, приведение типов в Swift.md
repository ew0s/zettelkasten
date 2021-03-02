# Свойства, типы данных, приведение типов в Swift
#Swift  

В этой статье будет пояснено устройство свойств и типов данных в __Swift__

---

 ## Свойства (константы и переменные)
 
 #### Константы
 
 Ключевое слово __let__ используется для того, что определить константу.
 
 ``` swift
 let constant = "This is a constant"
 ```
 
> Значение константы должно быть задано во время своего опеределения. 
> Послег того, как константа задана, ее значение менять нельзя.

#### Переменные

Ключевое слово __var__ используется для того, чтобы опеределить перемнную.
 
 ``` swift
 var variable
 variable = "This is a variable"
 ```
 
 > Переменная может менять свое значение в процессе работы программы.
 > Переменной можно не задавать значение во время ее опеределения.

---

## Базовые типы данных

#### String

Представляет собой набор значений из типа данных __character__

``` swift
var userName = "Michael"
print("His name is \(userName)")
```

Способы объявления строк:

```swift
var name: String  // nil
var surname = String()  // empty string
var email = ""  // empty string
```

##### Конкатенция строк

```swift
let fullName = name + " " + surname
var myName = "My name is "
myName += fullName
```

##### Интерполяция строк

```swift 
let numberOfLessons = 8
let currentLesson = 2

aboutCourse = """
Название: "Основы программирования на языке Swift"
Количество уроков: \(numberOfLessons)
Текущий урок: \(currentLesson)
Осталось уроков: \(numberOfLessons - currentLesson)
Автор и ведущий курса \(fullName)
"""

print(aboutCourse)
```

#### Int

```swift
var age = 10
```

> Размер зависит от разрядонсти системы

#### UInt

Swift также предусматривает беззнаковый тип целого числа - UInt, который имеет тот же размер что и разрядность системы.

#### Double

```swift
var someDouble = 12.9
```

> При присвоении переменной любого литерала с плавающей точкой, эта переменная имеет тип __Double__
> Весит 8 байт

#### Float

```swift
var someFloat: Float = 0.0

someFloat = 121.123444 // 121.1234
someFloat = 1221.123444 // 1221.123
```

>Для становления переменной этому типу данных, необходимо явно преобразовать эту перемнную к этому типу, при объявлении этой перемнной.
> Весит 4 байта

#### Boolean

```swift
let boolean = true
```

#### Псевдонимы типов

Псевдонимы типов_ задают альтернативное имя для существующего типа. Можно задать псевдоним типа с помощью ключевого слова typealias.

```swift
typealias AudioSample = UInt16
var maxAmplitudeFound = AudioSample.min // 0
```

---

## Приведение типов

```swift
age = 30

// Новая константа с типом Double
let castIntToDouble = someNumber + Double(age)

// Новая константа с типом Int
let castDoubleToInt = Int(someNumber) + age

// Приведение числовых значений к строковым данным
let myAge = "I'm "
let castIntToString = myAge + String(age) + " years old"

//Приведение строковых данных к числовым значениям
let someString = "10"
let castStringToInt = age + (Int(someString) ?? 0)
```

> (Int(someString) ?? 0) - в данном примере, оператор ?? - оператор объединения по __nil__. Извлекает опционал слева, если он содержит значение, или возвращает значение по умолчанию справа, если значение слева равно __nil__.

