# Динамика нелинейных робототехнических систем
## Homework 1: Прямая и обратная кинематика
Здесь будет какой-то текст позднее.

## Homework 2: ROS
| Команда  | Описание |
|  `cd ~/catkin_ws`  | Запуск системы  |
|  `catkin_make`  |   |
|  `source devel/setup.bash`  |   |
### Установка DOCKER и ROS1 в Ubuntu

| Команда  | Описание |  ?)    |
|-------|-----|-------|
| `echo $ROS_DISTRO` | Проверить установку ROS  |  |
| `rospack list`   | Проверить доступные пакеты  |    |
| `roscore`   | Запустить ROS  |    |
| `rosrun rviz rviz`   | Тестирование графических инструментов (RVIZ)  |    |
| `rospack list`   | Проверить доступные пакеты  |    |
|  `rosnode list`  |  Просмотр активных узлов |    |
|  `rostopic list`  | Просмотр топиков  |    |
|  `rosservice list`  |  Просмотр сервисов |    |

## Создание проекта
| Команда  | Описание |
|-------|-----|
|  `mkdir -p ~/catkin_ws/src`  |  Создание рабочей папки |
|  `cd ~/catkin_ws`  |   |
|  `catkin_make`  | Инициализация  |
|  `echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc`  | Настройка окружения  |
|  `cd ~/catkin_ws/src`  | Создание ROS пакета  |
|  `catkin_create_pkg my_robot rospy roscpp std_msgs geometry_msgs`  |   |
|  `cd ~/catkin_ws`  |   |
|  `source devel/setup.bash`  |   |
|  `cd ~/catkin_ws/src/my_robot`  |  Создание структуры проекта |
|  `mkdir urdf launch scripts`  |   |
|  `urdf/my_robot.urdf`  |  Создание URDF файла |
|  `scripts/robot_controller.py`  |  Создание Python контроллера |
|  `chmod +x ~/catkin_ws/src/my_robot/scripts/robot_controller.py`  | - отредактировать файлик  |
|  `launch/display.launch`  |  Создание Launch файла |
|  `rosrun rviz rviz -d ~/catkin_ws/src/my_robot/urdf/robot.rviz`  | Настройка RVIZ  |
|  `cd ~/catkin_ws`  | Запуск системы  |
|  `catkin_make`  |   |
|  `source devel/setup.bash`  |   |
|  `roslaunch my_robot display.launch`  |   |
|  `sudo apt install liburdfdom-tools`  |  Визуализация URDF структуры |
|  `cd ~/catkin_ws/src/my_robot/urdf`  |   |
|  `urdf_to_graphiz my_robot.urdf`  |   |
|  `check_urdf ~/catkin_ws/src/my_robot/urdf/my_robot.urdf`  | Проверка URDF  |

- my_robot.pdf - графическое представление
- my_robot.gv - текстовое описание

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
