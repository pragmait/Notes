## Переменные-ссылки
Есть переменные **==примитивного типа==** (**primitive type variables**) и **==ссылочные переменные==** (**reference variables**).
В отличие от примитивных типов, которые **позволяют хранить значения прямо внутри переменных**, переменные ссылочных типов хранят **==ссылки на объекты==.** Т.е. где-то в памяти существует некий объект, а в переменной-ссылке просто хранится адрес этого объекта в памяти (ссылка).
Значения прямо внутри переменных хранят только примитивные типы, **все** остальные типы хранят только ссылку на объект. Ранее вы уже, кстати, сталкивались с двумя такими типами переменных — это переменные типа `String` и переменные типа массив.
И массив, и строка являются объектами, которые хранятся где-то в памяти. Переменные типа `String` и переменные типа массив хранят только ссылки на объекты.

![[Pasted image 20240911115727.png]]

Переменные `int a, int b и double d` — примитивные и хранят значение внутри себя.
Переменная `String str` — ссылочная и хранит адрес (ссылку) объекта типа `String` в памяти.
При присваивании примитивного значения переменной примитивного типа, его значение **==копируется (дублируется)==**. При присваивании же ссылочной переменной **==копируется только адрес объекта, сам же объект при этом не копируется==**.

## Присваивание ссылок
При присваивании ссылочных переменных происходит просто **присваивание** адреса объекта в памяти. Сами объекты при этом не появляются и не исчезают.
Такой подход позволяет избежать копирования больших объемов памяти. Если куда-то нужно передать очень большой объект, мы просто передадим в этот метод ссылку на объект и все. Ссылка занимает гораздо меньше места.

![[Pasted image 20240911121322.png]]

Размер всех переменных-ссылок (независимо от типа) одинаков и составляет 4 байта (как тип int). Но! Если ваше приложение запущено на 64-х разрядной Java-машине, размер всех ссылок будет 8 байт (64 бита).
Ссылки при этом можно только присваивать друг другу. Вы не можете менять ссылки или присваивать им произвольные значения:

![[Pasted image 20240911121349.png]]

## Пустая ссылка — `null`

А что хранит переменная-ссылка, если ей еще ничего не присвоили?
А хранит она **пустую ссылку** — null. `null` — **==это специальное ключевое слово в Java==**, обозначающее **отсутствие ссылки** (пустую ссылку). Значение `null` можно присвоить любой ссылочной переменной.
Все переменные-ссылки, если им не присвоена какая-нибудь ссылка, имеют значение `null`.

![[Pasted image 20240911123020.png]]

Локальные переменные без значения считаются **неинициализированными** как для примитивных типов, так и для типов-ссылок.
Если переменная хранит ссылку на какой-то объект, а вы хотите стереть значение переменной, просто присвойте ей ссылку null.

![[Pasted image 20240911123202.png]]

## Передача ссылок в методы
Если у какого-нибудь метода есть параметры **==ссылочные переменные==**, передача значений в них происходит точно так же, как и при работе с обычными переменными. Переменной-параметру просто присваивается значение другой переменной.

![[Pasted image 20240911123448.png]]

При вызове метода `fill` переменной `array` присваивается ссылка на массив `data`. Переменной `value` присваивается ссылка на объект-строку «Hello».
Вот как будет выглядеть ситуация в памяти **перед вызовом метода** `fill`:

![[Pasted image 20240911123526.png]]

Вот как будет выглядеть ситуация **во время работы метода** `fill`:

![[Pasted image 20240911123545.png]]

Переменные `data` и `array` ссылаются (хранят ссылки) на один и тот же массив-контейнер в памяти.
Переменная `value` хранит ссылку объекта строки `Hello`.
Ячейки массива тоже хранят просто ссылки на объект `Hello`.
Фактически никакого дублирования объектов не происходит — копируются только ссылки.

>[!tip] Важно
>В Java этой двойственности нет, и правильный ответ звучит так: **параметры в методы Java передаются по значению**. Просто в случае с ссылочными переменными это значение — ссылка.

