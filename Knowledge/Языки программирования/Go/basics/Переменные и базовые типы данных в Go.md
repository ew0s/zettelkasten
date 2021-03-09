# Переменные и базовые типы данных в Go
#Go

В этой статье будут описаны переменные и базовые типы данных в Go

---

#### Переменные

```Go
// Значение по умолчанию
var num0 int

// Значение при инициализации
var num1 int = 1

// Пропуск типа
var num2 = 20
fmt.Println(num0, num1, num2)

// Короткое определение переменной
num := 30
// Только для новых переменных

num += 1
fmt.Println("num += 1 = ", num)

// Оператора ++ в Go нет
```

###### Стиль наименований

> Принято использовать __camelCase__

Те же самые правила работают для объявления нескольких переменных.

---

#### Типы данных в Go

##### Базовые

* int - платформенно-зависимый (32 или 64 бита)
  * int8
  * ...
  * int64
  * uint
* float32
* float64
* bool
* complex128

##### Строки в Go

```Go
// Со спец символами
var hello string = "Hello\n\t"

// Без спец символов
var word string = `Hello\n\t`
```

Строки из коробки поддерживают __utf-8__

##### rune и byte

* rune - uint32 для utf-8
* byte - uint8 для utf-8

__Строки в Go неизменяемые__

```Go
// Получение длины строки
helloWorld := "Привет Мир"
helloWorld[0] = 72
byteLen := len(helloWorld) // 19 байт
symbols := utf8.RuneCountInString(helloWorld) // 10 рун 

// Получение подстроки, в байтах, не символах!
hello := helloWorld[:12] // Привет, 0-11 байты
H := helloWorld[0] // byte, 72, не "П"

// Конвертация в слайс байт и обратно
byteString = []byte(helloWorld)
helloWorld = string(byteString)
```

---

#### Переменные

```Go
// Одиночное объявление
const pi = 3.141

// Множественное объявление
const (
    hello = "Привет",
    e     = 2.718
)
```

###### iota

__iota__ сделана для того, чтобы автоматически инкриминировать

```Go
// iota
const (
    zero = iota
    _       // Пустая переменная, пропуск iota
    three // = 3
)
```

```Go
const (
    _       = iota
    KB uint64 = 1 << (10 * iota)
    MB
)
```

```Go
const (
    // Нетипизированная константа
    year = 2017
    // Типизированная константа
    yearTyped int = 2017
)
```

```Go
func main() {
    var month int32 = 13
    fmt.Println(month + year)

    // month + yearTyped (mismatched types int32 and int)
    fmt.Ptintln( month + yearTyped )
}
```
