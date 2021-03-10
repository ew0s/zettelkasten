# Функции и замыкания в  Swift

#Swift

В этой статье будет рассказано об устройстве функций в __Swift__

---

### Функции

```swift
func nameOfFunction() {
    some code
}
```

#### Функции с возвращаемыми значениями

```swift
func nameOfFunction() -> Data Type {
    some code
    return some value
}
```

#### Функции с параметрами

```swift 
func name(argumentOne parameterOne: Data Type, argumentTwo parameterTwo: Data Type) {
    some code
}
```

Функция может содержать аргументы и параметры в своей сигнатуре. Аргументы и параметры связаны тем, что аргументы служат представлением параметров при вызове функции пользователем.
* Аргумент - это то, как будет ассоциироваться параметр у пользователя.
* Параметр - это то, с какими переменными будет работать функция внутри своего блока кода.

---

### Вариативные параметры

```swift
func arithmeticMean(_ numbers: Double...) -> Double {
    var total = 0.0

    for number in numbers {
        total += number
    }

    return total / Double(numbers.count)
}

arithmeticMean(1, 2, 3, 4, 5)
```

---

### Функции как замыкания

```swift
func filterWithPredicateClosure(value: Int, numbers: [Int], closure: (Int, Int) -> Bool) -> [Int] {
    var filterNumbers: [Int] = []

    for number in numbers {
        if closure(number, value) {
            filterNumbers.append(number)
        }
    }
    return filterNumbers
}
```

В этом примере ```swift closure: (Int, Int) -> Bool``` - это замыкание, то есть мы теперь можем передавать в параметры функции какую-либо функцию, которая совпадает по сигнатуре с сигнатурой замыкания.

##### Отбор чисел меньше указанного значения

```swift
func lesThenValue(number: Int, value: Int) -> Bool {
    number < value
}
```

```swift
filterWithPredicateClosure(value: 5, numbers: numbers, closure: lesThenValue)
```

---

### Замыкающие выражения

Замыкания бывают трех видов:
* Глобальные функции - это замыкания, которые имеют имя и которые не захватывают никакие значения.
* Вложенные функции - это замыкания, у которых тоже есть имя, но при этом они могут использовать или захватывать значения из родительской функции.
* Замыкающие выражения - это безымянные функции, которые написаны в облегченном синтаксисе, которые могут захватывать значения из окружающего контекста.

```swift
{ (параметры) -> тип результата in
    тело замыкающего выражения
}
```

##### Использование замыкания в качестве аргумента

```swift
filterWithPredicateClosure(
    value: 5,
    numbers: numbers,
    closure: { (number: Int, value: Int) -> Bool in
        return number < value
    }
)
```

##### Вывод типа из контекста

```swift
filterWithPredicateClosure(
    value: 5,
    numbers: numbers,
    closure: { (number, value) in
        return number < value
    }
)
```

##### Неявные возвращаемые значения из замыканий с одним выражением

```swift
filterWithPredicateClosure(
    value: 5,
    numbers: numbers,
    closure: { (number, value) in number < value }
)
```

##### Сокращенные имена параметров

```swift
filterWithPredicateClosure(
    value: 5,
    numbers: numbers,
    closure: { $0 < $1 }
)
```

##### Последующее замыкание

```swift
filterWithPredicateClosure(value: 5, numbers: numbers) { $0 < $1 }
```

##### Операторные функции

```swift
filterWithPredicateClosure(value: 5, numbers: numbers, closure: <)
```