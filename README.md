# Динамика нелинейных робототехнических систем
## Homework 1: Прямая и обратная кинематика
Здесь будет какой-то текст позднее.

## Homework 2: ROS
### Установка DOCKER и ROS1 в Ubuntu

# Проверить версию ROS
echo $ROS_DISTRO - проверить установку ROS

# Проверить доступные пакеты ROS
rospack list

# Запустить ROS
roscore

# Тестирование графических инструментов (RVIZ)
rosrun rviz rviz

# Полезные команды
## Просмотр активных узлов
rosnode list

## Просмотр топиков
rostopic list

## Информация о топике
rostopic echo /turtle1/pose

## Просмотр сервисов
rosservice list

# Создать папку для рабочих проектов
## Создайте рабочую папку ROS
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws

## Инициализируйте workspace
catkin_make

## Настройте окружение
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc


Шаг 1: Создание ROS пакета
bash
cd ~/catkin_ws/src
catkin_create_pkg my_robot rospy roscpp std_msgs geometry_msgs
cd ~/catkin_ws
catkin_make
source devel/setup.bash
Шаг 2: Создание структуры проекта
bash
cd ~/catkin_ws/src/my_robot
mkdir urdf launch scripts
Шаг 3: Создание URDF файла
Создать файл: urdf/my_robot.urdf

Содержит:

4 звена (base_link, link1, link2, link3)

3 вращательных шарнира (joint1, joint2, joint3)

Геометрия: куб, цилиндры, сфера

Материалы разных цветов

Шаг 4: Создание Python контроллера
Создать файл: scripts/robot_controller.py

Функциональность:

Инициализация ROS узла

Публикация состояний шарниров

Синусоидальное движение

Частота обновления: 10Hz

bash
chmod +x ~/catkin_ws/src/my_robot/scripts/robot_controller.py
Шаг 5: Создание Launch файла
Создать файл: launch/display.launch

Компоненты:

Загрузка URDF модели

Запуск joint_state_publisher

Запуск robot_state_publisher

Запуск RVIZ

Запуск контроллера

Шаг 6: Настройка RVIZ
bash
rosrun rviz rviz -d ~/catkin_ws/src/my_robot/urdf/robot.rviz
Действия в RVIZ:

Добавить RobotModel

Добавить TF

Сохранить конфигурацию

Шаг 7: Запуск системы
bash
cd ~/catkin_ws
catkin_make
source devel/setup.bash
roslaunch my_robot display.launch
Шаг 8: Визуализация URDF структуры
bash
sudo apt install liburdfdom-tools
cd ~/catkin_ws/src/my_robot/urdf
urdf_to_graphiz my_robot.urdf
Создает файлы:

my_robot.pdf - графическое представление

my_robot.gv - текстовое описание

Шаг 9: Запись видео демонстрации
bash
sudo apt install -y ffmpeg
ffmpeg -video_size 1920x1080 -framerate 25 -f x11grab -i :0.0 -c:v libx264 output.mp4
Структура проекта
text
my_robot/
├── CMakeLists.txt
├── package.xml
├── urdf/
│   ├── my_robot.urdf
│   └── robot.rviz
├── launch/
│   └── display.launch
├── scripts/
│   └── robot_controller.py
└── README.md
Команды проверки
bash
# Проверка URDF
check_urdf ~/catkin_ws/src/my_robot/urdf/my_robot.urdf

# Просмотр топиков
rostopic echo /joint_states

# Список узлов
rosnode list

# Список топиков
rostopic list
Описание робота
Структура:

Базовое звено: куб

Звено 1: цилиндр

Звено 2: цилиндр

Звено 3: сфера

Типы соединений:

3 вращательных шарнира

Цепная структура

Управление:

Синусоидальное движение

Разные частоты для каждого шарнира

Автоматическое циклическое движение
