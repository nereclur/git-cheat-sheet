# Инструкция по использованию GIT

### Навигация
- `pwd` (от англ. _**p**rint **w**orking **d**irectory_, «показать рабочую папку») — покажи, в какой я папке;
- `ls` (от англ. _**l**i**s**t directory contents_, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
- `ls -a` — покажи также скрытые файлы и папки, названия которых начинаются с символа `.`;
- `cd first-project` (от англ. _**c**hange **d**irectory_, «сменить директорию») — перейди в папку `first-project`;
- `cd first-project/html` — перейди в папку `html`, которая находится в папке `first-project`;
- `cd ..` — перейди на уровень выше, в родительскую папку;
- `cd ~` — перейди в домашнюю директорию (`/Users/Username`);
- `cd /` — перейди в корневую директорию.
-----
### Работа с файлами и папками

**Создание**

- `touch index.html` (англ. _touch,_ «коснуться») — создай файл `index.html` в текущей папке;
- `touch index.html style.css script.js` — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
- `mkdir second-project` (от англ. _**m**a**k**e **dir**ectory_, «создать директорию») — создай папку с именем `second-project` в текущей папке.

**Копирование и перемещение**

- `cp file.txt ~/my-dir` (от англ. _**c**o**p**y_, «копировать») — скопируй файл в другое место;
- `mv file.txt ~/my-dir` (от англ. _**m**o**v**e_, «переместить») — перемести файл или папку в другое место.

**Чтение**

- `cat file.txt` (от англ. _con**cat**enate and print_, «объединить и распечатать») — распечатай содержимое текстового файла `file.txt`.

**Удаление**

- `rm about.html` (от англ. _**r**e**m**ove_, «удалить») — удали файл `about.html`;
- `rmdir images` (от англ. _**r**e**m**ove **dir**ectory_, «удалить директорию») — удали папку `images`;
- `rm -r second-project` (от англ. _**r**e**m**ove,_ «удалить» + _**r**ecursive_, «рекурсивный») — удали папку `second-project` и всё, что она содержит.
----
### Полезные возможности

- Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (`&&`).
- У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (**`↑`**) и вниз (**`↓`**).
- Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать `Tab`. Если файл или папка есть в текущей директории, командная строка допишет путь сама.  
    Например, вы находитесь в папке `dev`. Начните вводить `cd first` и дважды нажмите `Tab`. Если папка `first-project` есть внутри `dev`, командная строка автоматически подставит её имя. Останется только нажать `Enter`.
----
### Инициализация репозитория

`git init` (от англ. _**init**ialize_, «инициализировать») — инициализируй репозиторий.

----

### Подготовка файла к коммиту

- `git add todo.txt` (от англ. _add_, «добавить») — подготовь файл `todo.txt` к коммиту;

- `git add --all` (от англ. _add_, «добавить» + _all_, «всё») — подготовь к коммиту сразу все файлы, в которых были изменения, и все новые файлы;

- `git add .` — подготовь к коммиту текущую папку и все файлы в ней.

----

### Создание коммита

`git commit -m "Комментарий к коммиту."` (от англ. _commit,_ «совершать», «фиксировать» + _**m**essage,_ «сообщение») — сделай коммит и оставь комментарий, чтобы было проще понять, какие изменения внесены.

----
### Просмотр информации о коммитах

`git log` (от англ. _log_, «журнал [записей]») — выведи подробную историю коммитов.

----
### Просмотр состояния файлов

`git status` (от англ. _status_, «статус», «состояние») — покажи текущее состояние репозитория.

----
### Конфигурация Git
- `git config` - просмотр настроек
- `git confil` --global user.name/email - установка имени/емейла глобально, для всех проектов
- `git config` --unset user.email/name - удалить локальные емейл/имя для проекта
- `git config` --global core.editor - установка текстового редактора гита
- `git config` --global aliac.c config - создать алиас c на команду config
- `git init` создать git файл в проекте
- `git add` - добавить файл в буфер гита 

-----
### Связывание репозитория
- `git init`
- `git add README.md`
- `git commit -m "first commit"`
- `git remote add origin`
- `git push -u origin main`

-----
### HEAD
Файл HEAD (англ. _head_ «голова», «головной») — один из служебных файлов папки .git. Он указывает на коммит, 
который сделан последним (то есть на самый новый).
-----
### Статусы`untracked`/`tracked`,`staged` и `modified`

Одна из ключевых задач Git — отслеживать изменения файлов в репозитории.
Для этого каждый файл помечается каким-либо статусом. Рассмотрим основные.

- **`untracked`** (англ. «неотслеживаемый»)  
  Новые файлы в Git-репозитории помечаются как `untracked`, то есть неотслеживаемые. Git «видит»,
  что такой файл существует, но не следит за изменениями в нём. У `untracked`-файла нет предыдущих версий,
  зафиксированных в коммитах или через команду `git add`.
- **`staged`** (англ. «подготовленный»)  
  После выполнения команды `git add` файл попадает в **staging area** (от англ. _stage_ — «сцена»,
  «этап [процесса]» и _area_ — «область»), то есть в список файлов, которые войдут в коммит.
  В этот момент файл находится в состоянии `staged`.

💡 Staging area также называют **index** (англ. «каталог») или **cache** (англ. «кеш»),
а состояние файла `staged` иногда называют `indexed` или `cached`.
Все три варианта могут встречаться в документации и в качестве флагов команд Git.
А также в интернете — например, в вопросах и ответах [на сайте Stack Overflow](https://stackoverflow.com/).

- **`tracked`** (англ. «отслеживаемый»)  
  Состояние `tracked` — это противоположность `untracked`. Оно довольно широкое по смыслу: в него попадают файлы,
  которые уже были зафиксированы с помощью `git commit`, а также файлы,
  которые были добавлены в staging area командой `git add`. То есть все файлы,
  в которых Git так или иначе отслеживает изменения.
- **`modified`** (англ. «изменённый»)  
  Состояние `modified` значит, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия.
  Например, файл был закоммичен и после этого изменён.


- Для файлов в состояниях `staged` и `modified` обычно не указывается, что они также `tracked`,
  потому что это состояние подразумевается.
- Команда `git add` добавляет в staging area только текущее содержимое файла. Если вы, например,
  сделаете `git add file.txt`, а затем измените `file.txt`, то новое содержимое файла не будет находиться в staging.
  Git сообщит об этом с помощью статуса `modified`: файл изменён относительно той версии, которая уже в staging.
  Чтобы добавить в staging последнюю версию, нужно выполнить `git add file.txt` ещё раз.