## Приведение типов

Переменные примитивных типов (за исключением типа `boolean`) используются для хранения разных типов чисел. И хоть типы переменных всегда неизменны, есть место, где можно **проводить преобразование типов**. **==И место это — присваивание==**.
Можно присваивать друг другу переменные разных типов. При этом значение, взятое из переменной одного типа, будет преобразовано в значение другого типа и присвоено второй переменной. В связи с этим можно выделить два вида преобразования типов: расширение и сужение.
==**Расширение типа**== похоже на перекладывание из маленькой корзинки в большую — операция проходит незаметно и безболезненно. ==**Сужение типа**== — это перекладывание из большой корзинки в маленькую: места может не хватить, и что-то придётся выбросить.
Вот типы, отсортированные по размеру «корзинки»:

![[Pasted image 20240910153410.png]]

## Расширение типов
Часто может возникнуть необходимость присвоить переменной одного числового типа значение переменной другого числового типа. Как же это сделать?
==В Java есть 4 целочисленных типа:==

![[Pasted image 20240910153733.png]]

>[!tip] Важно
Переменной большего размера всегда можно присваивать переменные меньшего размера.
Такое преобразование, от типа меньшего размера к большему, называется **==расширением типа==**.

Переменной типа `long` спокойно можно присваивать переменные типа `int`, `short` и `byte`. Переменной типа `int` можно присваивать переменные типа `short` и `byte`. Ну и переменной типа `short` можно присваивать переменные типа `byte`.

![[Pasted image 20240910153957.png]]

**А что насчет вещественных чисел?**
С ними все аналогично — ==размер имеет значение==:

![[Pasted image 20240910153915.png]]

Переменной типа `double` можно без проблем присвоить переменную типа `float`. А вот с целочисленными типами интереснее.
Переменной типа `float` можно присвоить переменную любого целочисленного типа. Даже типа `long`, длина которого 8 байт. А переменной типа `double` можно присвоить вообще что угодно: переменную любого целочисленного типа и переменную типа `float`:

![[Pasted image 20240910154016.png]]Обратите внимание, что преобразование к вещественному типу может привести к потере точности из-за нехватки значащих цифр.
При преобразовании из целых чисел в дробные могут отбрасываться самые младшие части числа. Но т.к. смысл дробного числа в том, чтобы хранить приблизительное значение, такое присваивание разрешается.

## Сужение типов
А что насчет остальных вариантов? Что делать, если нужно переменной типа `int` присвоить значение переменной типа `long`?
Представьте, что переменная — это корзина. У нас есть корзины разных размеров: 1, 2, 4 и 8 байт. При перекладывании пирожков из меньшей корзины в большую проблем не будет. А вот при **перекладывании из большей в меньшую часть пирожков может потеряться**.
Это преобразование — от типа большего размера к меньшему — называют сужением типа. При таком присваивании часть числа может просто не поместиться в новую переменную и «остаться за бортом».
При сужении типа мы должны явно показать компилятору, что мы не ошиблись, и отбрасывание части числа сделано осознанно. Для этого используется оператор приведения типа. Это **имя типа в круглых скобочках**.
В таких ситуациях Java-компилятор требует от программиста указывать оператор преобразования типа. Выглядит в общем виде он так:

![[Pasted image 20240910154310.png]]

![[Pasted image 20240910154405.png]]В данном случае `a` равно `1`, и это кажется излишним. А что если бы `a` было больше?

![[Pasted image 20240910154425.png]]

Миллион отлично помещается и в тип `long`, и в тип `int`. А вот при присваивании миллиона переменной типа `short` два первых байта были отброшены, и остались только два последних байта. А при присваивании типу `byte` вообще остался один последний байт.
Устройство чисел в памяти:

![[Pasted image 20240910154531.png]]

### Тип `char`

Тип `char`, как и тип `short`, занимает два байта, но для их преобразования в друг друга всегда нужно использовать оператор приведения типа. Все дело в том, что тип `short` знаковый, и может содержать значения от `-32,768` до `+32,767`, а тип `char` беззнаковый, и может содержать значения от `0` до `65,535`.

В `char` нельзя сохранить отрицательные числа, которые могут храниться в `short`. А в `short` нельзя сохранить числа больше `32,767`, которые могут храниться в `char`.

## Тип выражения

А что делать, если в одном выражении используются переменные разных типов? Логичный ответ – их сначала нужно преобразовать к общему типу. Но какому?==**Конечно же, к большему.**==
В Java всегда происходит преобразование к типу большей размерности. Грубо говоря, сначала происходит расширение типа одного из участников операции, а уже затем операция со значениями одинаковых типов.
Если в выражении участвуют типы `int` и `long`, значение типа `int` будет преобразовано к типу `long` и только затем будет участвовать в операции:

![[Pasted image 20240910160737.png]]

### Числа с плавающей точкой

Если в выражении участвуют целое число и число с плавающей точкой (`float`/`double`), целое число будет преобразовано в число с **плавающей** точкой (`float`/`double`), и только потом будет выполнена операция над ними.
Если в операции участвуют `float` и `double`, то `float` будет преобразован к `double`. Что, собственно говоря, ожидаемо.

>[!tip] Важно
>Типы `byte`, `short`, `char` всегда преобразовываются в тип `int` при взаимодействии между собой. Не зря же тип `int` считается стандартным целочисленным типом.

Если умножить `byte` на `short`, будет `int`. Если умножить `byte` на `byte`, будет `int`. Даже если сложить `byte` и `byte`, будет `int`.

![[Pasted image 20240910161014.png]]

В общем случае при умножении числа длиной в 8 бит (1 байт) на число длиной в 8 бит (1 байт), мы получим число длиной 16 бит (2 байта)
Поэтому все операции с целыми типами, меньшими чем `int`, всегда сразу преобразовываются в тип `int`. И поэтому если вы захотите сохранить результат вычисления в переменную типа, меньше чем `int`, вам всегда нужно будет явно указывать операцию приведения типа.

![[Pasted image 20240910161058.png]]

## Важный нюанс
> [!tip] Важно
**Операция приведения типа имеет довольно высокий приоритет.**
Если вы хотите преобразовать к определенному типу все выражение, а не только один его элемент, то оборачивайте все выражение в круглые скобки и перед ними ставьте оператор приведения типа.

Поэтому если в выражении есть, допустим, сложение и операция приведения типа, она будет выполнена до сложения.

![[Pasted image 20240910161258.png]]

