# Paquete Roberto para ROS 2 Jazzy

Este paquete contiene la configuración necesaria para simular un robot **TurtleBot3 (Burger)** en **Gazebo** utilizando **ROS 2 Jazzy**.  
Incluye mundos personalizados, descripción del robot, mapas y configuraciones para sistemas de **SLAM (Cartographer)** y **Navegación (Nav2)**.

---

# Estructura del Paquete

Una vez creado, el paquete debe seguir esta estructura:

```
roberto/
├── CMakeLists.txt        # Configuración de compilación
├── package.xml           # Metadatos del paquete y dependencias
├── launch/               # Archivos de lanzamiento (.py)
├── worlds/               # Definiciones de mundos de Gazebo (.world)
├── urdf/                 # Descripción del robot (.urdf o .xacro)
├── models/               # Modelos 3D y mallas (incluye dependencias de TurtleBot3)
├── maps/                 # Archivos de mapas guardados (.yaml, .pgm)
├── rviz/                 # Configuraciones guardadas de RViz
├── params/               # Archivos de parámetros (YAML)
├── src/                  # Código fuente C++ (si aplica)
└── include/              # Cabeceras C++ (si aplica)
```

---

# Requisitos Previos

Antes de empezar, asegúrate de tener instalados los paquetes necesarios para **Cartographer** y **Nav2**.

```bash
# 1. Actualizar repositorios
sudo apt update

# 2. Instalar paquetes necesarios
sudo apt install ros-jazzy-turtlebot3-cartographer
sudo apt install ros-jazzy-nav2-map-server
```

---

# 1. Preparar el Workspace

Es recomendable limpiar compilaciones previas antes de comenzar.

```bash
cd ~/ROS2/turtlebot3_ws
rm -rf build/ install/ log/
```

Después entra en la carpeta `src` y crea el paquete:

```bash
cd ~/ROS2/turtlebot3_ws/src

ros2 pkg create roberto --build-type ament_cmake --dependencies rclcpp std_msgs sensor_msgs gazebo_ros turtlebot3_gazebo nav2_msgs cartographer_ros
```

---

# 2. Organizar los Archivos

Una vez creado el paquete, copia o crea las carpetas y archivos según la estructura definida anteriormente dentro de:

```
~/ROS2/turtlebot3_ws/src/roberto/
```

Ubicación recomendada de los archivos:

- **launch/** → archivo `roberto.launch.py`
- **worlds/** → archivos `.world`
- **urdf/** → archivos `.urdf` o `.xacro`
- **models/** → modelos 3D adicionales
- **maps/** → mapas `.yaml` y `.pgm`
- **rviz/** → configuraciones `.rviz`
- **params/** → parámetros YAML para Nav2 o Cartographer

---

# 3. Compilar el Paquete

Antes de compilar, es recomendable limpiar compilaciones previas.

```bash
cd ~/ROS2/turtlebot3_ws
rm -rf build/ install/ log/
```

Compilar únicamente el paquete `roberto`:

```bash
colcon build --packages-select roberto
```

---

# 4. Cargar el Entorno

Después de compilar, carga el entorno de ROS 2 y del workspace:

```bash
source /opt/ros/jazzy/setup.bash
source ~/ROS2/turtlebot3_ws/install/setup.bash
```

---

# Lanzar la Simulación

Define el modelo del robot (**TurtleBot3 Burger**) y ejecuta el launch file principal.

```bash
export TURTLEBOT3_MODEL=burger

ros2 launch roberto roberto.launch.py
```

---

# Notas

- Este paquete está diseñado para funcionar con **ROS 2 Jazzy**.
- Se recomienda utilizar **Gazebo** para la simulación.
- Asegúrate de que las dependencias de **TurtleBot3**, **Cartographer** y **Nav2** estén correctamente instaladas.
