![простите, кажется что-то пошло пошло не так](Git-logo.png)
# Работа с Git
## 1. Проверка наличия установленного Git
В терминале выполнить команду `git version`.

Если Git установлен, появится сообщение с информацией о версии программы.
Если Git не установлен - появится сообщение об ошибке.

## 2. Установка Git
Загружаем последнюю версию Git [с этого сайта](https://git-scm.com/downloads "перейти по ссылке").

Устанавливаем Git с настройками по умолчанию.

## 3. Настройка Git
При первом использовании Git необходимо представиться. Для этого в терминале нужно выполнить две команды:

> - `git config --global user.name` - имя пользователя английскими буквами
> - `git config --global user.email` - email пользователя

## 4. Инициализация репозитория
Получить репозиторий можно двумя способами:

1. В терминале переходим к папке, в которой хотим сосздать репозиторий. Выполняем команду `git init`. 
Команда `git init` выполняется только один раз для первоначальной настройки нового репозитория.

2. Клонировать существующий репозиторий Git из любого места. Сделать это можно командой `git clone <адрес репозитория>`.

## 5. Запись изменений в репозитории

После внесения любых изменений в репозиторий, из необходимо зафиксировать.
Для того, чтобы изменения могли быть зафиксированы, нужно использовать либо ручное сохранение файла (`CTRL+S`), либо включить автосохранение в Visual SC.

Для фиксации изменений последовательно используются следующие команды:
> - `git add` + название файла - подготовка изменений к фиксации
> - `git commit` - фиксация

Кроме того можно использовать объединённую команду `git commit -a -m` либо её сокращенную версию `git commit -am` с записью в кавычках комментария о внесенных изменениях.

> **Важно!** Команда `git commit` с параметрами `-a -m` / `-am` фиксирует изменения во всём репозитории, а не в отдельном файле.
>
> Если нужно внести изменеия в отдельный файл - используются команды `git add`, а затем `git commit`.

>**Важно!** Команда `git commit` с параметрами `-a -m` / `-am` не позволяет добавить файлы к отслеживанию.

Посмотреть состояние репозитория и убедиться, что изменения зафиксированы можно командой `git status`.

Просмотреть отличия между текущим файлом и последней фиксацией можно с помощью команды `git diff`.

## 6. Перемещение между сохранениями

В случае необходимости можно вызвать любое из предыдущих сохранений документа.

Для это сперва нужно командой `git log` либо `git log --oneline` *(вывод одной строкой)* вызвать историю всех коммитов.

> `git log -p` - объединенная команда для `git log` и `git diff`
`git log -2` - выводит последние 2 коммита

Далее, для перемещения к нужному коммиту используется команда `git checkout` **+хешкод или имя коммита**, к которому нужно переместиться.

Для того, чтобы вернуться к актуальной версии, можно использовать одну из двух команд:
```
git switch
```
либо
```
git checkout master
```

## 7. Игнорирование файлов
Для того, чтобы исключить файлы и папки из отслеживания в репозитории, необходимо создать там файл ***.gitignore*** и записать в него их названия или шаблоны (расширения), соответствующие таким файлам и папкам.
Например, *.png - будет исключать из отслеживания все файлы в формате .png

## 8. Создание веток Git
**Ветка в Git** - это простой перемещаемый указатель на один из коммитов. Обычно последний в цепочке коммитов.
По умолчанию имя основной ветки в Git - *master*.

Создать ветку можно одной из двух команд:
1. `git branch` + название ветки
2. `git checkout -b` + название ветки

В результате создается новый указатель на текущий коммит.

## 9. Слияние веток в Git
Слияние веток позволяет объединить две ветки с разными версиями файла в одну ветку.

Для выполнения слияния нужно ввести команду `git merge` + имя ветки, с которой хотим добавить информацию в основную ветку.

После выполнения слияния его необходимо закоммитить.

>Если коммит слияния ещё не выполнен, отменить слияние можно двумя командами:
>
>`git merge --abort`
>
>`git reset --merge`

## 10. Удаление веток в Git
Для удаления ветки достаточно выполнить команду `git branch -d` +имя ветки.

Однако, если изменения из этой ветки не были слиты в основную ветку, Git может не захотеть удалять эту ветку.

В таком случае выходов два:
1. слить ветку, закоммитить и удалить
2. выполнить принудительное удаление ненужной ветки (если информация в ней нам совсем не нужна) командой `git branch -D` +имя ветки.

## 11. Разрешение конфликтов
В случае, если в основной и дополнительной ветках были сделаны и закоммичены изменения, при попытке слить ветку может возникнуть конфликт.

В этом случае достаточно выбрать версию, которую необходимо сохранить как верную, либо внести изменения и сохранить их в обеих ветках.

После чего необходимо закоммитить слияние веток.