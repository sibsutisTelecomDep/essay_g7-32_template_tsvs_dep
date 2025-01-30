# Оригинальный шаблон
Копия русскоязычного шаблона для рефератов по ГОСТ 7.32-2017 "Отчет о научно-исследовательской работе". Оригинал не был найден на github, только в Overleaf ([оригинальный шаблон ИТМО](https://ru.overleaf.com/latex/templates/essay-template-itmo-rus/qfhzpzxstvvw) ).

> Шаблон составлен для компилятора XeLaTeX, некоторые возможности которого (в частности, нативная поддержка Unicode) отсутствуют на более старом компиляторе pdfLaTeX. Поэтому, если вы компилируете при помощи pdfLaTeX, и у вас ничего не работает - не удивляйтесь. Все или почти все современные дистрибутивы LaTeX уже содержат внутри себя XeLaTeX, просто выберите его в настройках.

> Библиография собирается при помощи движка biber. Если компилятор выдает ошибку, либо же ссылки и/или список литературы выглядят не так, как должны - проверьте в настройках, нужный ли движок у вас подключен. В Overleaf специально выбирать ничего не надо, все работает по умолчанию. В некоторых сборках движок для библиографии надо выбирать вручную в настройках (например, в TeXstudio по умолчанию стоит bibTeX).

> Оригинально щаблон подготовлен в Overleaf, но его работоспособность также проверялась на Windows 11 в связке MikTeX + TeXstudio.
# Написание отчетов\стетей (Latex) в редакторе VSCode

<img src="https://github.com/user-attachments/assets/a0d59ae8-b444-4cd4-a48f-9215845b5b93" width="950" />

Для такого результата необходимо установить:


1. VSCode. Потребуется x64 версия;
2. MiKTEX;
3. Strawberry Perl;
4. Поддержка XeLaTeX в VSCode;
5. Расширения для VSCode: LaTeX Workshop, LaTeX Utilities.

## Установка (Windows)
### 1. VSCode
[VSCode](https://code.visualstudio.com/). Ничего сверхъестественного, скачиваем, устанавливаем. 
### 2. MiKTEX
Страница загрузки [MiKTeX](https://miktex.org/download). Скачиваем, устанавливаем. 

> Важное замечание! При установке НЕ меняйте стандартный путь установки.

<img src="https://github.com/user-attachments/assets/698ca3ae-de16-46a3-ab04-75f32f6e6a53" width="600" />


После установки, проверить и установить обновления.

<img src="https://github.com/user-attachments/assets/78fc5978-0dfc-4d72-8ffb-fc1556a4238c" width="600" />


### 3. Strawberry Perl
Устанавливаем крайний релиз [Strawberry Perl](https://strawberryperl.com/), в моем случае - 5.40.0.1.

Ничего не меняем при установке. 

### 4. Проверка переменных окружения
После установки MiKTeX и Strawberry Perl переменные окружения должны добавиться самостоятельно, все же, желательно проверить: `System Properties` -> `Advanced` -> `Environment Variables...` -> `System Variables` -> `Path` -> `Edit`.

<img src="https://github.com/user-attachments/assets/7e1cc1b1-1515-4ad3-b97d-efd6449a79ec" width="600" />



### 5. VSCode Extensions: LaTeX Workshop, LaTeX Utilities

Устанавливаем расширения VSCode:

<img src="https://github.com/user-attachments/assets/ca51d44b-c6ec-4cf2-af4d-df32cfb64a2f" width="600" />


### 6. Поддержка xelatex
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
1. После установки и настройки VSCode скачиваем репозиторий (можно просто `ZIP-архив`):
```sh
git clone https://github.com/sibsutisTelecomDep/essay_g7-32_template_tsvs_dep.git
```
2. Открываем папку в VSCode.
3. Переходим в расширение TeX, выполняем команду `Build`, получаем в корневой папке `.pdf-файл` проекта.

<img src="https://github.com/user-attachments/assets/4ac12dd7-0da0-4f4b-8ea4-01b1b3b7bac8" width="900" />
