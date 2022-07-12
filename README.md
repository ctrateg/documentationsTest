# documentationsTest

## Краткое описание того, как это повторить

Ссылочка https://ctrateg.github.io/documentationsTest/documentation/documentationstest/

Работает в принципе как jazzy, то есть пишешь комментарии через /// и он их видит, вносит локально, ты можешь обратится к базовой документации проекта, там все будет со ссылками и т.д. 
Но стоит учитывать тот факт, что берет только публичные элементы 

## Создание документации

А теперь по пунктам самого создания публичной документации их всего 2

### Создаст пул файлов из билджа документации и нужного нам .doccarchive, с которым мы потом взаимодействовать будем 

``` "xcodebuild docbuild \                 
-scheme documentationsTest \                                 
-derivedDataPath ~/Desktop \
-destination 'platform=iOS Simulator,name=iPhone 13'

В принципе стандартный билд доки где 3 строка указывает путь

Но любопытный кейс, можно просто экспортировать файл .doccarchive из локальной документации, но без сторонних файлов билда(или же просто он экспортирует коряво) не получается нормально сконфигурировать для github pages наши файлы в следующем пункте 

### Далее создания уже js файлов документации

``` (xcrun --find docc) process-archive \
transform-for-static-hosting documentationsTest.doccarchive \
--output-path docs \
--hosting-base-path documentationsTest ```

По строчно
1) запускает создание
2) указывается местонахождение .doccarchive файла 
3) уже место где файлы будут созданны
4) название репозитория

На самом деле можно в принципе это все в мейке автоматизировать и жизнь облегчится

Вытаскивать саму доку(как можно заметить) через documentation/documentationstest/ где название проекта без кэмела

### Вывод 

Сама дока удобнаа, есть кейсы у знакомых, которые используют на опен проектах собранных из package'ов и в основном именно на пакетах, есть кейсы где внедряли на средних проектах уже крупные фирмы, но опять же субьективная вещь, но жирный плюс в виде локальной документации, но все таки минус(а для кого то и нет) что только паблик сегменты(но и тут в теории, но не на практике, если пощупать можно найти способ это обойти, но это предположение, надо серчить)

P.S. Если все таки разобраться чутка то мне кажется у меня просто не получилось через експорт с локальной доки вытащить докфайл и с таким способом жизнь упростится, но уже надо прям смотреть
P.S.S В принципе если автоматизируют, то можно спокойно переезжать как и на SPM(меньше сторонних либ плюс в карму всегда)

### Не много ссылочек сразу

Удобный но затянутый ролик можно на 1.5 смотреть:
https://www.youtube.com/watch?v=8KoIXbm0nv4

Статейка где все получилось без первого пункта(но у меня не особо)
https://www.createwithswift.com/publishing-docc-documention-as-a-static-website-on-github-pages/

Оригинал стати выше
https://apptractor.ru/develop/publikuem-dokumentatsiyu-docc-v-vide-sayta-github-pages.html
