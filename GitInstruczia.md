![Тут должно быть лого](GitPosts-1080x675.png)
# Инструкция по Git

## 1. Проверка наличия установленного Git

В терминале выполняем команду git version.

Если Git если гит установлен, то появиться сообщение с информацией о версии файла, иначе будет сообщение об ошибке. 
![Выглядит это так](12.JPG)

## 2. Установка Git

Смотрим видео и делаем по видео:

для [Windows](https://gbcdn.mrgcdn.ru/uploads/record/53869/attachment/3de0ac7e50a023626dbcec71fbaa44ae.mp4) и для 
[MacOs](https://gbcdn.mrgcdn.ru/uploads/record/53868/attachment/4b8ca2920c7b990110e62a60cfbfbb21.mp4)

Ссылка для скачивания последней версии с [сайта](https://git-scm.com/)

## 3. Настройка Git

При первом использовании Git необходимо представиться, для этого ввсти две команды:

git config --global user.name "[name]"

git config --global user.email "[emai addresы]"

Для того чтобы проверить прошла ли регистрация надо ввести команду: git config --list

## 4. Инициализация Репозитория

Прописываем  в терминале команду git init.

 В исходной папке в скрытых появиться папка .git
![Выглядит это так](12.JPG)

## 5. Проверка статуса репозитория

Просмотреть статус нужного репозитория можно по ключевому слову status: его действие распространяется на подготовленные, неподготовленные и неотслеживаемые файлы.

git status

## 6. Добавление файла в индекс

 Добавить отдельный файл в область подготовленных файлов можно параметром add с указанием имени файла. Просто начните писать название файла, а дальше нажмите "Tab" и выберите нужнцй файл двигая стрелочки вверх.

git add [название файла]

***После ввода этой команды вы можете сделать коммит.***

>Есть похожие команды, например:

 > git add . индексирует сразу все изменённые файлы и папки в директории, где вы находитесь. Обратите внимание, между точкой и словом add нужно ставить пробел. 
 
 > git add :/ добавляет в индекс все файлы независимо от того, в какой директории вы находитесь.

## 7. Внесение изменений однострочным сообщением 

При создании коммита в репозитории можно добавить однострочное сообщение с помощью параметра commit с флагом -m. Само сообщение вводится непосредственно после флага, в кавычках.

git commit -m "Your short summary about the commit"

git commit -am "Name of commit" - *закоммитить отслеживаемые индексированные файлы (указано название коммита, не требует git add, не добавит в коммит неотслеживаемые файлы)*

## 8. Просмотр истории коммитов с изменениями

Просматривать изменения, внесённые в репозиторий, можно с помощью параметра log. Он отображает список последних коммитов в порядке выполнения. Кроме того, добавив флаг -p, вы можете подробно изучить изменения, внесённые в каждый файл.

 git log -p

 git log --oneline  - *эта команда позволит видеть сокращённый список коммитов.* 
 
 Выглядит это так
 ![Сокращённый коммит](Сокращённый_коммит.JPG)

## 9. Просмотр изменений до коммита

Можно просматривать список изменений, внесённых в репозиторий, используя параметр diff. По умолчанию отображаются только изменения, не подготовленные для фиксации.

git diff

## 10. Временно переключиться на другой коммит

git checkout b9533bb - *временно переключиться на коммит с указанным хешем*

git checkout master - *вернуться к последнему коммиту в указанной ветке*

## 11 Добавление картинок и игнорирование файлов

Для того чтобы разместить картинку в нашем файле надо добавить её в папку и после этого пишем в нужнм месте следуюее:
! [подписи картинок](название файла с расширением)

Для того чтобы удалить файлы с изображениями с отслеживания надо создать файл .gitignore
 
 И внести в него изображение, чтобы не вносить множество изображений в файл прописываем те расширения, которые должен Git игнорировать. Например: *.JPG и *.png

## 12 Ветвление

Для создания новой ветки надо ввести в терминале команду git branch name_branch

Ветвление необходимо для работы с файлами в отдельной ветке, сохраняя при этом исходное состояние файла до слияния.

Чтобы отобразить созданные ветки, используется команда git branch.

Чтобы перейти на другую ветку используем команду git checkout name_branch

## 13 Слияние веток 

Для слияния веток и внесения изменения в наш основной файл используется команда git merge name_branch

Слияние делается в ту ветку в которой мы находимся на данный момент.
При слиянии возможны конфликты мы сейчас пробуем их создать.

Конфликт возникает при слиянии дух веток при этом дожна быть изменена одна и таже строка файла.

конфликт выглядит вот так

![конфликт](Конфликт_1.JPG)

Для решения конфликта необходимо выбрать вариант из списка над строкой <<<<<< HEAD (Текущее изменение). Если нужен свой вариант, то стереть <<<<< , ======= и выбрать те строки которые необходимы, а ненужные удалить. 

## 14 Переписывание истории

**Команда *git commit --amend* и другие способы переписать историю**

В Git существует несколько механизмов хранения истории и сохранения изменений. Вот эти механизмы: *commit --amend*, *git rebase* и *git reflog*. 

Команда *git commit --amend* — это удобный способ изменить последний коммит. Она позволяет объединить проиндексированные изменения с предыдущим коммитом без создания нового коммита.

![фотография команды](Изменение_коммита.JPG)

**Не используйте amend для публичных коммитов**

>Измененные коммиты по сути являются новыми коммитами. При этом предыдущий коммит не останется в текущей ветке. Последствия этой операции аналогичны сбросу (reset) публичного состояния кода. Не изменяйте коммит, после которого уже начали работу другие разработчики. Эта ситуация только запутает разработчиков, и разрешить ее будет непросто.

**Для изменения старых или нескольких коммитов** 
используйте команду *git rebase* для объединения нескольких коммитов в новый базовый коммит. В стандартном режиме команда git rebase позволяет в буквальном смысле перезаписать историю: она автоматически применяет коммиты в текущей рабочей ветке к указателю head переданной ветки. Поскольку новые коммиты заменяют старые, команду git rebase запрещено применять к коммитам, которые стали доступны публично. Иначе история проекта исчезнет. 

## 15 Просмотр лога (истории) в консоли в виде дерева

Для просмотра лога коммитов можно воспользоваться следующей командой:

git log --graph --color-words --color --source --decorate --all

В результате в текстовом виде будет выведено дерево коммитов и веток, причем вывод будет иметь цветовую раскраску. Будут хорошо выделены теги, разным цветом будут выделены ветки, будет показано местонахождение в проекте (HEAD), если в настоящий момент произошел откат до какого-нибудь коммита.

Выглядеть это будет так
![Дерево](Дерево.JPG)

Вот еще один удобный вариант. Дерево с номерами коммитов и их описаниями:

git log --graph --oneline --all

А это выглядит так
![Дерево второй вариант](Дерево_1.JPG)

Более короткий вид, который позволяет удобнее смотреть именно дерево. В нем один коммит занимает одну строку:

git log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all

Вид
![Дерево третий вариант](Дерево_2.JPG)

И последний вариант. 

Полный граф коммитов c сокращёнными хешами, ссылками на коммиты и абсолютной датой. Используемый формат: синий сокращённый хеш коммита, голубая абсолютная дата, зелёная относительная дата, жёлтые ссылки на коммит, перевод строки, белые сообщение и автор:

git log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all

Вид 
![Дерево четвёртый вариант](Дерево_3.JPG)

# Работа с удалёнными репозиториями
 
 1. Заходим в репозиторий с которым хотим работать, нажимаем на кнопочку Fork ![так выглядит кнопка](Fork.JPG)
 2. Отжимаем галочку ![Картинка](Галочка.JPG)
 3. Затем копируем ссылку ![](Ссылка.JPG)
 4. Заходим в папку в которую хотим скопировать репозиторий на локальном компьютере. В терминале прописываем команду: *git clone ссылка* 
 5. Заходим в Терминале в нужную папку через команду: *cd <название папки>*
 6. **Создаём новую ветку**(обязательно) при помощи команды: *git branch название ветки*, следующей командой переходим на эту ветку: *git checkout название ветки*.
 Можно одной командой:  ***git checkout -b "название ветки***
 7. Создаём файл, что-то в нём правим и всё по плану, команды: status, add, commit.
 8. Заливаем изменения на GitHab при помощи команды: *git push*. Смотрим на подсказки Git ![фото](Команда_push.JPG) копируем команду, вставляем и переходим.
 9. Отправляем изменённый файл, тому над чьим репозиторием мы работали с помощью кнопки Pull request ![так она выглядит](Pull_request.JPG)

 ## Команда *pull* 

 git pull тоже самое что и git fetch + git merge. Разумеется, что изменения будут объединяться с соответствующими ветками: master с origin/master, feature с origin/feature. Ветки объединяются не по имени, как кто-то может подумать, а за счёт upstream tracking branch. Когда мы делаем checkout любой ветки для работы, git делает приблизительно следующее:
смотрит есть ли уже такая ветка локально и если есть берёт её
если ветки нет, смотрит есть ли она удалённо origin/<branch_name>
если есть, создаёт локально <branch_name> там же, где и origin/<branch_name> и «связывает» эти ветки (branch <branch_name> now is tracking remote origin/<branch_name>)

В файле .git/config можно это увидеть:
[branch "master"]
        remote = origin
        merge = refs/heads/master


В 95% случаев, вам не нужно менять это поведение.

Если были локальные изменения, то git pull автоматически объединит их с удалённой веткой и будет merge-commit, а не fast-forward. Пока мы что-то разрабатывали код устарел и неплохо было бы сначала обновиться, применить все свои изменения уже поверх нового кода и только потом отдать результат. Или пока продолжить локально. И чтоб история не смешивалась. Вот это и помогает делать rebase.
Чтобы git по умолчанию использовал rebase, а не merge, можно его попросить:
git config branch.<branch_name>.rebase true