roberto/
├── CMakeLists.txt      # Configuración de compilación
├── package.xml         # Metadatos del paquete y dependencias
├── launch/             # Archivos de lanzamiento (.py)
├── worlds/             # Definiciones de mundos de Gazebo (.world)
├── urdf/               # Descripción del robot (archivos .urdf o .xacro)
├── models/             # Modelos 3D y mallas (incluye dependencias de TurtleBot3)
├── maps/               # Archivos de mapas guardados (.yaml, .pgm)
├── rviz/               # Configuraciones guardadas de RViz
├── params/             # Archivos de parámetros (YAML)
├── src/                # Código fuente C++ (si aplica)
└── include/            # Cabeceras (si aplica)



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

2. Compilar el Paquete

Compila específicamente el paquete roberto usando colcon:

Bash

colcon build --packages-select roberto

3. Cargar el Entorno
Este paso es obligatorio en cada nueva terminal para que ROS 2 reconozca el paquete:

Bash

source /opt/ros/jazzy/setup.bash
source install/setup.bash

4. Lanzar el Mundo
Define el modelo del robot y lanza el archivo principal:

Bash

export TURTLEBOT3_MODEL=burger
ros2 launch roberto roberto.launch.py


develop
