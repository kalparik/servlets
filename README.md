# Домашнее задание к занятию «2.1. Servlet Containers»

## CRUD

### Легенда

В рамках лекции мы реализовали практически полноценный In-Memory CRUD-сервер (Create Read Update Delete) на базе сервлетов. Этому серверу не хватает двух вещей:

1. Привести код в должный вид: вынести методы в константы, убрать дублирующийся код.
1. Реализовать репозиторий — пока вместо репозитория установлена заглушка.

### Задача

1. Осуществите рефакторинг кода.
1. Реализуйте репозиторий с учётом того, что методы репозитория могут вызываться конкурентно, т. е. в разных потоках.

Как должен работать `save`:

1. Если от клиента приходит пост с id=0, значит, это создание нового поста. Вы сохраняете его в списке и присваиваете ему новый id. Достаточно хранить счётчик с целым числом и увеличивать на 1 при создании каждого нового поста.
1. Если от клиента приходит пост с id !=0, значит, это сохранение (обновление) существующего поста. Вы ищете его в списке по id и обновляете. Продумайте самостоятельно, что вы будете делать, если поста с таким id не оказалось: здесь могут быть разные стратегии.


## WebApp Runner* (задача со звёздочкой)

Это необязательная задача, её выполнение не влияет на получение зачёта.

### Легенда

Не всегда удобно «таскать» за собой полноценный Tomcat: скачивать его, распаковывать и т. д. Достаточно часто используют библиотеку [WebApp Runner](https://github.com/heroku/webapp-runner), ранее (com.github.jsimone webapp-runner).

Встраивание WebApp Runner в ваш проект позволяет запускать его таким образом: `java -jar target/dependency/webapp-runner.jar target/<appname>.war`. Это достаточно удобно для размещения на облачных платформах.

### Задача

Добавьте в свою сборку скачивание `webapp-runner` согласно [инструкции](https://github.com/heroku/webapp-runner#using-with-maven-in-your-project).

Убедитесь, что сборка проходит, и ваш war-файл действительно запускается указанной выше командой.

### Результат

Реализуйте новую функциональность в ветке `feature/webapp-runner` вашего репозитория из предыдущего домашнего задания и откройте Pull Request.

В качестве результата пришлите ссылку на ваш Pull Request на GitHub в личном кабинете студента на сайте [netology.ru](https://netology.ru).

После того, как домашнее задание будет принято, сделайте `merge` для Pull Request.