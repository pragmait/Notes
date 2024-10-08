## Арифметические операции
- сложение (знак +)
- вычитание (-)
- умножение (*)
- деление (/).
## Операции сравнения.
- равно (` == `)
- больше (`>`)
- меньше (`<`)
- больше либо равно (`>=`)
- меньше либо равно (`<=`)
- не равно (`!=`)

> [!tip] Запомни
> Запомни: присваивание осуществляется справа налево.

## Унарные операции
Они называются “унарными” от слова “uno” — “один”. Такое название они получили потому, что в отличие от предыдущих, ==проводятся над одним числом, а не над несколькими==.

- Унарный минус. Он меняет знак числа на противоположный. (`-`)
- Инкремент (`++`)
- декремент (`--`)

> [!tip] Важный момент
> Операции инкремента и декремента бывают двух видов: **постфиксными**, и **префиксными**.
> `x++` — постфиксная запись 
> `++x` — префиксная запись

## Комбинированные операции
- `+=`
- `-=`
- `*=`
- `/=`
- `%=`

## Логические операции
Помимо операций над числами, в Java существуют также операции над булевыми переменными — `true` и `false`.

[[Логические операции if, and, or]]

- `!` — оператор “НЕ”. Меняет значение булевой переменной на противоположное
- `&&` — оператор “И”. Возвращает значение `true` только в том случае, если оба операнда являются `true`. Оператору `&&` для того, чтобы вернуть `true` требуется, чтобы истинными были все условия (как во второй строке, например).
- `||` — оператор “ИЛИ”. Возвращает `true`, когда хотя бы один из операндов истинный.