# Этот репозиторий поможет тебе разобраться в GIT и GITHUB

### С помощью GIT ты можешь делать локальные snapshot своего проекта

### А с помощью GITHUB ты можешь выложить свой локальный репозиторий в интернет

## Шпаргалка: командная строка
Мы подготовили для вас небольшую шпаргалку. Если забудете команды, просто возвращайтесь к этому уроку. Некоторые команды из списка мы не проходили, так что пробегитесь по нему глазами, даже если хорошо помните предыдущий урок.
- `pwd` — покажи в какой я папке;
- `ls` — покажи файлы в папке, где я сейчас;
- `cd first-project` — перейди в папку `first-project`;
- `cd first-project/html` — перейди в папку html, находящуюся в папке `first-project`;
- `cd ..` — перейди на уровень выше в родительскую папку;
- `cd ~` — перейди в домашнюю директорию (у нас это `/Users/stas_basov`);
- `mkdir second-project` — в текущей папке создай папку с именем `second-project`;
- `rm about.html` — удали файл `about.html`;
- `rmdir images` — удали папку `images`;
- `rm -r second-project` — удали папку `second-project` и всё, что она содержит;
- `touch index.html` — создай файл `index.html` в текущей папке;
- `touch index.html style.css script.js` — если нужно создать несколько файлов, их имена можно вводить через пробел.
Чтобы не вводить названия файлов и папок полностью, можно начать вводить их имя и нажать клавишу Tab. Командная строка допишет путь сама, если соответствующий файл или папка есть в текущей директории.
Например, находясь в папке `dev` начните вводить `cd first` и нажмите Tab. Если папка `first-project` есть внутри `dev`, командная строка автоматически подставит её имя. Останется только нажать Enter.

## Шпаргалка: Git
Запомнить все команды сразу невозможно. А цикл коммита всегда одинаковый. Мы подготовили ещё одну шпаргалку, на случай если вы забыли, что за чем идёт.
#### Команды для синхронизации локального репозитория с удалённым.
`git remote add origin https://github.com/YandexPracticum/first-project.git` — находясь в папке с локальным репозиторием, привязываем его к удалённому (URL у вас будет свой);
`git push -u origin main` — заливаем все файлы из локального репозитория в удалённый, который уже привязали.
#### Команды для того чтобы сделать сохранение — коммит.
`git add название_файла` — готовим выбранный файл к коммиту;
`git add -A` — чтобы ничего не потерять, можно подготовить к коммиту сразу все файлы, в которых были изменения;
`git commit -m "комментарий к коммиту"` — делаем коммит. К сохранённым файлам оставляем комментарий для того, чтобы проще было понять, какие сделаны изменения.
#### Команды для публикации изменений:
`git pull` — забрать изменения, сделанные другими разработчиками;
`git push` — опубликовать изменения в удалённый репозиторий.

### Типичный жизненный цикл файла в Git

Может показаться, что файлы в репозитории попадают в разные состояния хаотично. На практике это не так, и у большинства файлов вполне предсказуемый путь.

!https://pictures.s3.yandex.net/resources/M2_T5_1686651284.png

1. Файл только что создали. Git ещё не отслеживает содержимое этого файла. Состояние: `untracked`.
2. Файл добавили в staging area с помощью `git add`. Состояние: `staged` (+ `tracked`).
    - Возможно, изменили файл ещё раз. Состояния: `staged`, `modified` (+ `tracked`).
    Обратите внимание: `staged` и `modified` у одного файла, но у разных его версий.
    - Ещё раз выполнили `git add`. Состояние: `staged` (+ `tracked`).
3. Сделали коммит с помощью `git commit`. Состояние: `tracked`.
4. Изменили файл. Состояние: `modified` (+ `tracked`).
5. Снова добавили в staging area с помощью `git add`. Состояния: `staged` (+ `tracked`).
6. Сделали коммит. Состояния: `tracked`.
7. Повторили пункты 4−7 много-много раз.

    4−7
