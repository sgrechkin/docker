# Отчет по практической работе модуля 5 - Виртуализация и контейнеризация.
## В данной работе будет описан процесс запуска простой программы на языке Python в контейнере Docker

### Установка Docker и Docker Compose
- Добавляем репозиторий Docker в источники Apt и устанавливаем docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin.
- Для удобства добавляем пользователя в группу docker, что позволит запускать команды без повышения прав.
- Скачиваем, устанавливаем и даём права на исполнение для [Docker Compose](https://github.com/docker/compose).
- Проверяем версии установленных пакетов командами **docker --version** и **docker-compose --version**.

### Разработка простой программы
- В качестве программы для запуска в контейнере будем использовать консольный вариант игры ["Змейка"](https://github.com/GeorgeZhukov/python-snake/blob/master/snake.py).

### Подготовка Docker и Docker Compose
- Скачиваем образ командой **docker pull osrf/ros:humble-desktop**.
- Создаём **Dockerfile** (комментарии внутри файла).
- Командой **docker build -t custom_ros_image .** (точка в конце команды сообщает о том, что Doсkerfile находится в текущей директории) собираем новый образ с именем custom_ros_image.
- В папке с проектом создаём файл **docker-compose.yaml** (комментарии внутри файла).

### Запуск программы в контейнере
- Запускаем Docker Compose командой **docker-compose up**
- Подключаемся к запущенному контейнеру командой **docker-compose exec snake bash**
- Командой **python3 /home/snake.py** запускаем программу (выход по нажатию клавиши Esc)
- В результате должнен запуститься консольный вариант игры в "Змейку"
![Скриншот работающей программы](https://github.com/sgrechkin/docker/blob/main/screen.png)

### Завершение работы
- Командой **docker-compose down** останавливаем и удалям все запущенные сервисы.
