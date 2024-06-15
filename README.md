# Guide to Git, или знакомство с Git

В данной статье будут рассказаны основы работы с Git – от установки до использования основных команд.

## Настройка окружения и знакомство с командной строкой

### Установка командной строки для пользователей Windows

Командная строка — один из основных инструментов взаимодействия с компьютером. 

Windows поставляется с консолью — как и другие операционные системы. Но при этом команды консоли Windows и macOS/Linux отличаются друг от друга. Для того чтобы работать в Git с помощью консоли, необходимо установить специальный консольный инструмент для Windows, который называется **Git Bash**.

Вот что нужно сделать:

1. Перейдите [на эту страницу официального сайта Git](https://git-scm.com/download/win).

2. Скачайте одну из двух версий из категории **Standalone Installer** (англ. «автономный установщик»). Узнать тип вашей системы Windows можно в настройках.

   ![img](https://pictures.s3.yandex.net/resources/S1_57-4_1683900281.png)

3. Запустите программу установки. Обратите внимание, куда будет установлен Git. Обычно это директория`C:\Program Files\Git`.

   ![img](https://pictures.s3.yandex.net/resources/S1_gal_1-1_1683900369.png)

4. Проверьте, что в списке устанавливаемых программ стоит галочка напротив пункта **Git Bash Here** — это позволит открывать консоль с Git в любой папке.

   ![img](https://pictures.s3.yandex.net/resources/S1_gal_1-3_1683900499.png)

5. Далее установщик предложит много опций. Для нашего курса достаточно оставить все настройки по умолчанию. Несколько раз нажмите **Next** (англ. «далее»), пока не начнётся процесс установки.

6. После окончания установки нажмите **Finish** (англ. «завершить»).

Запустите программу Git Bash. Сделать это можно двумя способами. Можно ввести название программы в окно поиска на панели задач.

![img](https://pictures.s3.yandex.net/resources/S1_03-3_1683900547.png)

А можно открыть директорию, в которую был установлен Git. Обычно это директория `C:\Program Files\Git\bin`. Перейдите в `bin` и запустите файл `bash.exe`.

![img](https://pictures.s3.yandex.net/resources/S1_03-2_1683900567.png)

Откроется консоль, в которой будет написано что-то похожее.

![img](https://pictures.s3.yandex.net/resources/S17_31_1683900588.png)

Вместо `USER_NAME` будет указано ваше имя пользователя, а вместо `HOST_NAME` — имя компьютера. Если вы видите консоль, значит, установка прошла успешно.

### Установка командной строки для пользователей macOS или Linux

Если вы пользователь macOS или Linux, двигайтесь дальше, так как командная строка у вас уже установлена по умолчанию.

### Знакомство с командной строкой

Если вы пользователь macOS или Linux, запустите программу **Terminal**. Её можно найти через окно поиска операционной системы. А можно использовать комбинацию горячих клавиш:

- для Linux — `Ctrl+Alt+T`;
- для macOS — `Cmd+Space`, затем ввести `terminal`.

Если вы пользователь Windows, запустите программу Git Bash.

В зависимости от операционной системы порядок компонентов и внешний вид строки могут немного различаться.

Так это будет выглядеть в Windows и Linux.

```bash
userName@ComputerName ~ 
```

А так — в macOS.

```bash
computerName:~ userName$ 
```

В командной строке вы тоже всегда находитесь в какой-то папке — просто этого не видно. Узнать, где вы сейчас, поможет команда `pwd` (от англ. ***p**rint **w**orking **d**irectory* — «показать рабочую папку»). Она выводит путь к текущей директории.

Введите `pwd` в командную строку и нажмите клавишу `Enter` для выполнения команды.

```bash
$ pwd
/c/Users/%USERNAME%
/Users/%USERNAME% 
```

С помощью терминала вы всегда можете перейти к домашней директории. Для этого нужно ввести команду `cd` (от англ. ***c**hange **d**irectory* — «сменить директорию») и символ `~` — обозначение домашней директории. Не забудьте про `Enter` для выполнения.

```bash
$ cd ~ 
```

### Установка Git

Для установки Git на macOS откройте консоль и выполните команду `/usr/bin/git`. Она запустит установщик. Нажмите **Install** и дождитесь окончания установки.

![image](https://pictures.s3.yandex.net/resources/S1_57-5_1683929261.png)

Когда установка завершится, для проверки выполните эту команду.

```bash
$ git version
```

Если на экран выводится текущая версия Git, значит, установка прошла успешно.

## Настройка Git

Сейчас вы работаете в одиночку, но в дальнейшем вам может понадобиться использовать Git в команде. Чтобы участникам проекта было понятно, кто и какие изменения вносил, нужно представиться и указать имя пользователя и адрес электронной почты.

Вы можете указать любую электронную почту и любое имя. Сделать это можно с помощью команды `git config`  с ключом `--global`. При этом не имеет значения, в какой директории вы находитесь прямо сейчас: вызов `git config --global` сработает везде.

В качестве значения `user.name` нужно указать своё имя или никнейм. Для настройки параметра `user.email` указывают электронную почту.

```bash
$ git config --global user.name "User Namovich" 
# имя или ник нужно написать латиницей и в кавычках

$ git config --global user.email username@yandex.ru
# здесь нужно указать свой настоящий email 
```

Все глобальные настройки Git хранит в файле `.gitconfig` в домашней директории. Команда запишет в этот файл указанные имя и почту. Чтобы убедиться в этом, можно вызвать команду для чтения файлов.

```bash
$ cat ~/.gitconfig
```

Другой способ проверки — вывести содержимое файла конфигурации Git той же командой `git config` с флагом `--list`.

```bash
$ git config --list 
```

В ответ командная строка покажет текущие значения настроек.

```bash
user.name=Username
user.email=username@yandex.ru 
```

## Инициализируем репозиторий

Чтобы Git начал отслеживать изменения в проекте, папку с файлами этого проекта нужно сделать **Git-репозиторием**. Для этого следует переместиться в неё и ввести команду `git init`.

Например, создайте папку `first-project` и сделайте её Git-репозиторием: перейдите в неё с помощью команды `cd` и выполните `git init`.

```bash
$ cd ~/dev/first-project # перешли в нужную папку

$ git init # создали репозиторий 
```

Если вы случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно удалить скрытую подпапку `.git`.

```bash
$ cd <папка с репозиторием> # перешли в папку

$ rm -rf .git # удалили подпапку .git 
```

Разберём подробнее, что такое `-rf`:

- ключ `-r` (от англ. ***r**ecursive* — «рекурсивно») позволяет удалять папки вместе с их содержимым;
- ключ `-f` (от англ. ***f**orce* — «заставить») избавит вас от вопросов вроде «Вы точно хотите удалить этот файл? А этот? И этот тоже?».

## Cостояние репозитория

После инициализации репозитория `first-project` запустите команду `git status` (от англ. *status* — «статус», «состояние») — она показывает текущее состояние репозитория.

Команда `git status` выведет:

- название текущей ветки: `On branch master` или `On branch main`;
- сообщение о том, что в репозитории ещё нет коммитов: `No commits yet`;
- сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это создать» — `nothing to commit (create/copy files and use "git add" to track)`.

## Добавляем файлы в репозиторий

Добавим в репозиторий два файла. Например, файл `todo.txt`, в котором будет список дел, и `readme.txt` для информации о проекте.

Сейчас в `first-project` два файла. Мы хотим отслеживать состояние обоих, поэтому можем использовать команду `git add --all` (от англ. *add* — «добавить» + от англ. *all* — «всё»). Ключ, или флаг, `--all` позволяет подготовить к сохранению все файлы в репозитории.

```bash
$ git add --all # подготовили к сохранению все файлы в репозитории
$ git status # проверили статус 
```

Добавлять файлы можно и по одному, без ключа `--all`.

```bash
$ git add todo.txt
$ git add readme.txt
$ git status 
```

Также можно добавить текущую папку целиком — в этом случае все файлы в ней тоже будут добавлены. Обратиться к текущей папке в Bash позволяет точка (`.`).

```bash
$ git add . # добавить всю текущую папку
$ git status 
```

## Делаем первый коммит

Коммит гарантирует, что изменения будут сохранены в истории и при необходимости к ним можно будет «откатиться».

Сделать коммит можно командой `git commit` c ключом `-m` (от англ. ***m**essage* — «сообщение»), который присваивает коммиту сообщение.

```bash
$ git commit -m 'Мой первый коммит!'
```

