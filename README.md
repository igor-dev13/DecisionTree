DecisionTree

1. Зайти в папку - 'build_index_file', сгенерировать index.html файл подав на вход xml файл.
Например: DecisionTree.Core.exe devops_sup.xml 

2. Перекинуть index.html в папку 'www'

3. Залить содержимое папки www на сервер. Приложение использует node.js Уставновить его и зависимости (npm install)

4. Запустить app.js как сервис, можно через приложение forever для node js. (npm install forever -g) 
Запускаем - forever start decisionTree.js

5. Создается сервер, который обслуживает порт 3000. Делаем редирект хоста на 3000 порт.
Пример для nginx
location ~ ^(.*) {
    proxy_pass http://127.0.0.1:3000$1$is_args$args;
}

Если xml файл будет обновляться, пересобираем index.html файл (пункт 1) и меняем его. При необходимости чистим историю переходов
в history.json файле. Без истории, он будет такой - {"table":[]}

Истрию переходов можно посмотреть в файле /history.csv