Разница колоссальная.

В первую очередь она в том, что `inline-block` продолжают участвовать в потоке, а `float` -- нет.

Чтобы её ощутить, достаточно задать себе следующие вопросы:

1. Что произойдёт, если контейнеру `UL` поставить рамку `border` -- в первом и во втором случае?
2. Что будет, если элементы `LI` различаются по размеру? Будут ли они корректно перенесены на новую строку в обоих случаях?
3. Как будут вести себя блоки, находящиеся под галереей?

Попробуйте сами на них ответить.

Затем читайте дальше.

Что будет, если контейнеру `UL` поставить рамку `border`?
: Контейнер не выделяет пространство под `float`. А больше там ничего нет. В результате он просто сожмётся в одну линию сверху.

    Попробуйте сами, добавьте рамку в [песочнице](sandbox:solution).

    А в случае с `inline-block` всё будет хорошо, т.к. элементы остаются в потоке.

Что будет, если элементы `LI` различаются по размеру? Будут ли они корректно перенесены на новую строку в обоих случаях?
: При `float:left` элементы двигаются направо до тех пор, пока не наткнутся на границу внешнего блока (с учётом `padding`) или на другой `float`-элемент.

    Может получиться вот так:

    ![](gallery-float-diffsize.png)

    Вы можете увидеть это, открыв [демо-галерею](gallery-float-diffsize/) в отдельном окне и изменяя его размер:

    При использовании `inline-block` таких странностей не будет, блоки перенесутся корректно на новую строку. И, кроме того, можно выровнять элементы по высоте при помощи `li { vertical-align:middle }`:

    [iframe height=500 src="gallery-inline-block" link edit]

Как будут вести себя блоки, находящиеся под галереей?
: В случае с `float` нужно добавить дополнительную очистку с `clear`, чтобы поведение было идентично обычному блоку.

    Иначе блоки, находящиеся под галереей, вполне могут "заехать" по вертикали на территорию галереи.

