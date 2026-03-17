# Proyecto Roberto - ROS 2 Jazzy

Este paquete contiene la configuración y los archivos necesarios para la simulación y navegación de un robot TurtleBot3 en ROS 2 Jazzy.

## Estructura del Proyecto

```text
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
```

## Requisitos e Instalación

### 1. Actualizar Repositorios
Antes de comenzar, asegúrate de tener los repositorios actualizados:
```bash
sudo apt update
```

### 2. Instalación de Dependencias
Instala los paquetes necesarios para Cartographer y el servidor de mapas de Nav2:
```bash
sudo apt install ros-jazzy-turtlebot3-cartographer
sudo apt install ros-jazzy-nav2-map-server
```

## Guía de Uso

### 1. Preparar el Workspace
Se recomienda realizar una limpieza de las compilaciones previas para evitar conflictos:
```bash
cd ~/ROS2/turtlebot3_ws
rm -rf build/ install/ log/
```

### 2. Compilar el Paquete
Utiliza `colcon` para compilar específicamente el paquete `roberto`:
```bash
colcon build --packages-select roberto
```

### 3. Cargar el Entorno
Este paso es obligatorio en cada nueva terminal para que ROS 2 reconozca el paquete:
```bash
source /opt/ros/jazzy/setup.bash
source install/setup.bash
```

### 4. Lanzar la Simulación
Define el modelo del robot (ej. `burger`) y lanza el archivo principal:
```bash
export TURTLEBOT3_MODEL=burger
ros2 launch roberto roberto.launch.py
```
