**int** — это сокращение от **Integer** (целый с английского), что как бы намекает, что этот тип позволяет хранить целые числа.
Переменные типа **int** способны хранить целые числа в диапазоне от ==**-2 миллиарда до +2 миллиарда==.** Или, если быть более точным, то **==от -2,147,483,648 до 2,147,483,647==**.

> [!info] Интересный факт
> Такие некруглые значения связаны с устройством памяти компьютера.
> В Java для типа **int** выделено ==**4 байта памяти**==. Каждый байт памяти состоит из ==8 битов==. Каждый бит может принимать только 2 значения — 0 или 1. Переменная типа **int** содержит ==32 бита== и может принимать **4,294,967,296** значений.
> Половину этого диапазона отдали под отрицательные числа, а вторую — под положительные. Вот и получилось как раз от **-2,147,483,648 до 2,147,483,647**.

## Создание переменной типа `int`
![[Pasted image 20240118005604.png]]

## Краткая запись создания переменных
Если в одном месте программы нужно создать много переменных одного типа, это можно сделать, используя сокращенную запись:
![[Pasted image 20240118005655.png]]
## Присваивание значений
Чтобы **занести значение** в **переменную** типа **int**, нужно воспользоваться командой:
![[Pasted image 20240118005844.png]]
## Сокращенная запись создания и инициализации переменной
**==Создание (объявление) переменной и присваивание ей значения==** можно записать **одной командой**. Чаще всего так и делают, т. к. переменная обычно объявляется тогда, когда возникает необходимость сохранить какое-либо значение.
![[Pasted image 20240118005936.png]]
Можно объявить и **==несколько переменных одной строкой==**. Тогда команда будет иметь вид:
![[Pasted image 20240118010034.png]]

## Операции над переменными типа `int`
В правой части от **==оператора присваивания==** (знака равенства) может быть любое выражение — комбинация чисел, переменных и знаков **==+, -, * , /==**.
Также можно использовать скобки `( )`. В Java, как и в математике, сначала вычисляются выражения внутри скобок, а затем — вовне.
**Умножение** и **деление** имеют **==равный приоритет==**, и он **==выше==**, чем у сложения и вычитания.
**==При деление на 0 возникает ошибка "Деление на ноль"==**

![[Pasted image 20240118011408.png]]

### Деление целых чисел
В Java при делении **целого числа** на **целое число** всегда получается **==целое число==**. Остаток от деления при этом отбрасывается. Или же можно сказать, что отбрасывается дробная часть.

![[Pasted image 20240118012604.png]]
### Остаток от деления целых чисел
Кроме сложения, вычитания, умножения и деления для целых чисел в Java есть еще и оператор «**остаток от деления**». Используется для этого ==символ процент – **%**==. Это именно **остаток от деления целого числа на целое**, а не дробная часть.

![[Pasted image 20240118012748.png]]

Это очень полезный оператор, и используется он довольно часто. Например, чтобы узнать, ==**четное число или нет**==, достаточно поделить его на **2** и полученный остаток **сравнить с нулем**. Если остаток от деления равен нулю, число **четное**, если равен единице — **нечетное**.
![[Pasted image 20240118012915.png]]

### Инкремент и декремент
В программировании очень часто приходится увеличивать или уменьшать переменную на единицу. Для этих действий в Java есть специальные команды:

Оператор **==инкремент==** (*увеличение на единицу*) выглядит так:
Эта команда делает то же самое, что и команда `a = a + 1;` – увеличивает переменную `a` на единицу.
![[Pasted image 20240118013329.png]]

Оператор **декремент** (*уменьшение на единицу*) выглядит так:
Эта команда делает то же самое, что и команда `a = a - 1;` – уменьшает переменную `a` на единицу.
![[Pasted image 20240118013514.png]]