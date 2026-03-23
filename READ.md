# Paquete Roberto para ROS 2 Jazzy

Este paquete contiene la configuración necesaria para simular un robot TurtleBot3 (Burger) en Gazebo utilizando ROS 2 Jazzy. Incluye mundos personalizados, descripción del robot, mapas y configuraciones para sistemas de SLAM (Cartographer) y Navegación (Nav2).

## Estructura del Paquete

Una vez creado, el paquete debe seguir esta estructura:


roberto/
├── CMakeLists.txt # Configuración de compilación
├── package.xml # Metadatos del paquete y dependencias
├── launch/ # Archivos de lanzamiento (.py)
├── worlds/ # Definiciones de mundos de Gazebo (.world)
├── urdf/ # Descripción del robot (archivos .urdf o .xacro)
├── models/ # Modelos 3D y mallas (incluye dependencias de TurtleBot3)
├── maps/ # Archivos de mapas guardados (.yaml, .pgm)
├── rviz/ # Configuraciones guardadas de RViz
├── params/ # Archivos de parámetros (YAML)
├── src/ # Código fuente C++ (si aplica)
└── include/ # Cabeceras (si aplica)


## Requisitos Previos

Antes de empezar, asegúrate de tener instalados los paquetes necesarios para Cartographer y Nav2:

# 1. Actualizar repositorios
sudo apt update

# 2. Instalación de paquetes necesarios para Cartographer y Nav2
sudo apt install ros-jazzy-turtlebot3-cartographer
sudo apt install ros-jazzy-nav2-map-server


1. Preparar el Workspace

Es recomendable realizar una limpieza de compilaciones previas antes de empezar:

Bash

cd ~/ROS2/turtlebot3_ws
rm -rf build/ install/ log/


cd ~/ROS2/turtlebot3_ws/src

# Crea el paquete con las dependencias principales
ros2 pkg create roberto --build-type ament_cmake --dependencies rclcpp std_msgs sensor_msgs gazebo_ros turtlebot3_gazebo nav2_msgs cartographer_ros


2. Organizar los Archivos
Una vez creado el paquete, copia o crea las carpetas y archivos según la estructura definida anteriormente dentro de ~/ROS2/turtlebot3_ws/src/roberto/:

launch/: Coloca aquí tu archivo roberto.launch.py.

worlds/: Coloca aquí tus archivos .world.

urdf/: Coloca aquí tus archivos .urdf o .xacro.

models/: Coloca aquí los modelos 3D adicionales (asegúrate de incluir los de TurtleBot3 si no están en el sistema).

maps/: Coloca aquí los archivos .yaml y .pgm de los mapas guardados.

rviz/: Coloca aquí las configuraciones de RViz (.rviz).

params/: Coloca aquí los archivos de parámetros YAML para Nav2 o Cartographer.

3. Compilar el Paquete

Antes de compilar, es recomendable realizar una limpieza de compilaciones previas:

bash
cd ~/ROS2/turtlebot3_ws
rm -rf build/ install/ log/

Compila específicamente el paquete roberto usando colcon:

bash
colcon build --packages-select roberto

4. Cargar el Entorno

source /opt/ros/jazzy/setup.bash
source install/setup.bash

#  Lanzar la Simulación
Define el modelo del robot (TurtleBot3 Burger) y lanza el archivo principal:

bash
export TURTLEBOT3_MODEL=burger
ros2 launch roberto roberto.launch.py


