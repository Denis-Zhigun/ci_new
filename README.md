# Описание счетчиков покрытия JaCoCo

## Инструкции (C0-покрытие)

Самая маленькая единица измерения JaCoCo - это одиночные инструкции кода байта Java. Покрытие инструкции предоставляет информацию о количестве кода, который был выполнен или пропущен. Эта метрика полностью независима от исходного форматирования и всегда доступна даже в отсутствие отладочной информации в файлах классов.

## Отрасли (C1 Покрытие)

JaCoCo также вычисляет охват веток для всех операторов if и switch. Эта метрика подсчитывает общее количество таких ветвей в методе и определяет количество выполненных или пропущенных ветвей. Распространение веток всегда доступно, даже при отсутствии отладочной информации в файлах классов.

Обратите внимание, что обработка исключений не рассматривается как ветки в контексте этого определения счетчика.

Если файлы классов были скомпилированы с информацией об отладке, точки принятия решений могут быть сопоставлены с исходными строками и подсвечены соответственно:

* Нет покрытия: нет ответвлений в линии (красный ромб)
* Частичное покрытие: выполнена только часть ветвей в линии (желтый ромб)
* Полное покрытие: все ответвления в линии выполнены (зеленый ромб)

## CYCLOMATIC COMPLEXITY

JaCoCo также вычисляет циклическую сложность для каждого не абстрактного метода и суммирует сложность для классов, пакетов и групп. Согласно его определению McCabe1996, циклическая сложность - это минимальное количество путей, которые могут в (линейной) комбинации генерировать все возможные пути с помощью метода. Таким образом, значение сложности может служить указанием на количество единичных тестовых случаев для полного покрытия определенного программного обеспечения. Показатели сложности всегда можно вычислить даже в отсутствие отладочной информации в файлах классов.

Формальное определение циклической сложности v (G) основано на представлении графа потока управления методом как ориентированного графа:

v(G) = E - N + 2

Где E - количество ребер, N - количество узлов. JaCoCo вычисляет циклическую сложность метода со следующим эквивалентным уравнением, основанным на числе ветвей (B) и числе точек решения (D):

v(G) = B - D + 1

Основываясь на состоянии покрытия каждой ветки, JaCoCo также вычисляет покрытую и пропущенную сложность для каждого метода. Пропущенная сложность снова указывает на то, что количество тестовых случаев отсутствует, чтобы полностью покрыть модуль. Обратите внимание, что поскольку JaCoCo не рассматривает обработку исключений, так как ветки try/catch блоки также не будут увеличивать сложность. линии

## LINE

Для всех файлов классов, которые были скомпилированы с информацией об отладке, можно рассчитать информацию о покрытии для отдельных строк. Исходная строка считается выполненной, когда была выполнена хотя бы одна команда, назначенная этой строке.

В связи с тем, что одна строка обычно компилируется в несколько команд с байтовым кодом, подсветка исходного кода показывает три разных состояния для каждой строки, содержащей исходный код:

* Нет покрытия: ни одна инструкция в строке не была выполнена (красный фон)
* Частичное покрытие: выполнена только часть инструкции в строке (желтый фон)
* Полное покрытие: все инструкции в строке выполнены (зеленый фон)