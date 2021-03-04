# Типы коллекций и циклы в __Swift__

#Swift

В этой статье описаны коллекции и циклы в __Swift__

---

#### Типы коллекций

### Массивы

```swift
// Неизменяемый массив с типом данных String
let strings = ["a", "b", "c"]

// Неизменяемый массив с типом данных Character
let characters: [Character] = ['a', 'b', 'c']

// Пустой массив с типом Int
var integers = [Int]()
var anotherIntegers: [Int] = []

// Присваивание данных массиву
integers = [1, 2, 3, 4]

// Теперь наш массив имеет другие данные
integers = [5, 6, 7, 8]

// Добавление новых значений к уже существующим
integers += [9, 10]

// Добавление нового значения при помощи метода append
integers.append(11)

// Добавление нового элемента по индексу
integers.insert(1. at: 0)

// Создание нового массива, путем объединения двух других массивов
anotherIntegers = integers + [12, 17]

// Удаление последнего элемента из массива и сохранение его в константе
anotherIntegers.removeLast()

// Результат после удаления последнего элемента
let constant = anotherIntegers.removeLast() // 12

// Удаление первого элемента
anotherIntegers.removeFirst()

// Удаления значения по индексу
anotherIntegers.removeAt(1)

// Количество элементов массива
anotherIntegers.count

// Удаление всех элементов массива
anotherIntegers.removeAll()

// Обнуление массива
integers = []

integers = [10, 20 , 40]

// Замена значения по индексу 2 на новое значение
integers[2] = 30
```

##### Использование логического свойства isEmpty

```swift
if !integers.isEmpty() {
    integers[0] = 10
}
```

---

### Множества
> Хранят в себе неупорядоченные, но при этом уникальные значения одного типа

```swift
// Создание пустого множества
var characters: Set<Character> = []
var integers = Set<Int>()

// Создание множества с типом String
var strings: Set = ["a", "b", "c", "c", "c", "d"] // b c a d

// Добавление нового элемента в множество
strings.insert("b") // inserted false
strings.insert("f") // inserted true

// Проверка на наличие определенного элемента в множестве
strings.contains("a") // true

// Сортировка с использованием метода sorted()
strings.sorted() // ["a", "b", "c", "d", "f"]
let anotherStrings = strings.sorted(by: >)
```
### Словари
> Коллекция ключ значение

```swift
// Инициализация словаря с данными
var someStringDictionary = Dictionary<String, String>()
var newStringDictionary = Dictionary<String, String> = [:]
var anotherSomeDictionary = [Int: String]()
var carWashQueue: [String: String] = [:]  //  best practice

// Наполнения словаря данными
carWashQueue = ["E095BA": "Red Toyota", "E012BA": "Black Toyota"]

// Изменение значения для ключа
carWashQueue["E095BA"] = "Red Camry"

// Изменение значения с сохранением строго значения
carWashQueue.updateValue("Gray BMW x6", forKey: "E012BA") // вернуло старое значение

// Добавление новой пары ключ - значение
carWashQueue["M0505R"] = "Green Chavy Niva"

carWashQueue.count

carWashQueue["M0505R"] = nil

// Удаление значения по ключу с сохранением значения
removeValue
removeAll
...
```


