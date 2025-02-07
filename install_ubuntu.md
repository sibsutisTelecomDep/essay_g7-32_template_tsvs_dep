### 1. VSCode
[VSCode](https://code.visualstudio.com/). Ничего сверхъестественного, скачиваем, устанавливаем. 
### 2. MiKTEX
Устанавливаем доп. зависимости:

```sh
sudo apt install curl git texlive-science texlive-latex-extra texlive-extra-utils latexmk texlive-publishers texlive-science
```

Страница загрузки [MiKTeX](https://miktex.org/download). Устанавливаем для своей версии операционной системы. 

> Следуйте инструкциям. Пример показан с установкой для всей системы




После установки, проверить и установить обновления.



### 3. Strawberry Perl
Устанавливаем крайний релиз [Strawberry Perl](), в моем случае - 5.40.0.1.

```sh
sudo apt-get update -y
sudo apt-get install perl -y
```

### 4. Установка шрифтов (для Times New Roman)

```sh
sudo apt-get install ttf-mscorefonts-installer

```



### 5. VSCode Extensions: LaTeX Workshop, LaTeX Utilities

Устанавливаем расширения VSCode:

<img src="https://github.com/user-attachments/assets/ca51d44b-c6ec-4cf2-af4d-df32cfb64a2f" width="600" />


### 6. Настройка "рецептов" xelatex
В проектах [Overleaf](https://ru.overleaf.com/project) используется верстка `xelatex`, добавим поддержку в VSCode: `CTRL`+`Shift`+`P`, далее ищем `Preferences: Open User Settings (JSON)` в открывшемся файле добавляем строки:
```sh
"latex-workshop.latex.recipes": [
  {
    "name": "latexmk",
    "tools": [
      "latexmk"
    ]
  },
],

"latex-workshop.latex.tools": [
  {
    "name": "latexmk",
    "command": "latexmk",
    "args": [
      "-xelatex",
      "-synctex=1",
      "--shell-escape",
      "-interaction=nonstopmode",
      "-file-line-error",
      "%DOC%"
    ],
    "env": {}
  },
  {
    "name": "pdflatex",
    "command": "pdflatex",
    "args": [
      "--shell-escape",
      "-synctex=1",
      "-interaction=nonstopmode",
      "-file-line-error",
      "%DOC%"
    ],
    "env": {}
  },
  {
    "name": "bibtex",
    "command": "bibtex",
    "args": [
      "--shell-escape",
      "%DOCFILE%"
    ],
    "env": {}
  }
]

```

## Компиляция, получение PDF
1. После установки и настройки VSCode скачиваем репозиторий (можно просто `ZIP-архив`):
```sh
git clone https://github.com/sibsutisTelecomDep/essay_g7-32_template_tsvs_dep.git
```
2. Открываем папку в VSCode.
3. Переходим в расширение TeX, выполняем команду `Build`, получаем в корневой папке `.pdf-файл` проекта.

<img src="https://github.com/user-attachments/assets/4ac12dd7-0da0-4f4b-8ea4-01b1b3b7bac8" width="900" />