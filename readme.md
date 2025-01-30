# Оригинальный шаблон
Копия русскоязычного шаблона для рефератов по ГОСТ 7.32-2017 "Отчет о научно-исследовательской работе". Оригинал не был найден на github, только в Overleaf ([оригинальный шаблон ИТМО](https://ru.overleaf.com/latex/templates/essay-template-itmo-rus/qfhzpzxstvvw) ).

> Шаблон составлен для компилятора XeLaTeX, некоторые возможности которого (в частности, нативная поддержка Unicode) отсутствуют на более старом компиляторе pdfLaTeX. Поэтому, если вы компилируете при помощи pdfLaTeX, и у вас ничего не работает - не удивляйтесь. Все или почти все современные дистрибутивы LaTeX уже содержат внутри себя XeLaTeX, просто выберите его в настройках.

> Библиография собирается при помощи движка biber. Если компилятор выдает ошибку, либо же ссылки и/или список литературы выглядят не так, как должны - проверьте в настройках, нужный ли движок у вас подключен. В Overleaf специально выбирать ничего не надо, все работает по умолчанию. В некоторых сборках движок для библиографии надо выбирать вручную в настройках (например, в TeXstudio по умолчанию стоит bibTeX).

> Оригинально щаблон подготовлен в Overleaf, но его работоспособность также проверялась на Windows 11 в связке MikTeX + TeXstudio.
# Написание отчетов\стетей (Latex) в редакторе VSCode

<img src="rmd_img/Overview.png" width="900">

Для такого результата необходимо установить:

1. VSCode. Потребуется x64 версия;
2. MiKTEX;
3. Strawberry Perl;
4. Расширения для VSCode: LaTeX Workshop, LaTeX Utilities.

## Установка (Windows)
### 1. VSCode
[VSCode](https://code.visualstudio.com/). Ничего сверхъестественного, скачиваем, устанавливаем. 
### 2. MiKTEX
Страница загрузки [MiKTeX](https://miktex.org/download). Скачиваем, устанавливаем. 

> Важное замечание! При установке НЕ меняйте стандартный путь установки.

<img src="rmd_img/miktex.png" width="600">

После установки, проверить и установить обновления.


<img src="rmd_img/miktex_update.png" width="600">

### 3. Strawberry Perl
Устанавливаем крайний релиз [Strawberry Perl](rmd_img/Overview.png), в моем случае - 5.40.0.1.

Ничего не меняем при установке. 

### 4. Проверка переменных окружения
После установки MiKTeX и Strawberry Perl переменные окружения должны добавиться самостоятельно, все же, желательно проверить: `System Properties` -> `Advanced` -> `Environment Variables...` -> `System Variables` -> `Path` -> `Edit`.

<img src="rmd_img/system_variables.png" width="400">


### 5. VSCode Extensions: LaTeX Workshop, LaTeX Utilities

Устанавливаем расширения VSCode:

<img src="rmd_img/vscode_extensions.png" width="400">

### 6. Поддержка latexmk
В проектах [Overleaf](https://ru.overleaf.com/project) используется верстка `xelatex`, добавим поддержку в VSCode: `CTRL`+`Shift`+`P`, далее ищем `Preferences: Open User Settings (JSON)` в открывшемся файле добавляем строки:
```sh
"latex-workshop.latex.tools": [{
        "name": "latexmk",
        "command": "latexmk",
        "args": [
            "-xelatex",
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "%DOC%"
        ]
    }],
```

## Компиляция, получение PDF
Переходим в расширение TeX, выполняем команду `Build`, получаем в корневой папке `.pdf-файл` проекта.
<img src="rmd_img/build.png" width="900">