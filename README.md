# Instalando e configurando MoveIt Motion Planning Framework.

![moveit logo](/images/moveit_logo.png)

A fim de instalar, configurar e executar simulações do Moveit Motion Planning Framework me fundamentei no seguinte artigo:

* [Getting Started — moveit_tutorials Noetic documentation](https://ros-planning.github.io/moveit_tutorials/doc/getting_started/getting_started.html)

Fluxograma para a instalação do MoveIt.<br/>
![flowchart install moveit](/images/flowchart_moveit.png)

---
Antes de fazer tais instalação do MoveIt é necessário ter o ROS-1 (Noetic) instalado, para isso vá até o artigo abaixo:

* [Instalando e configurando ROS-1 (Noetic) e Gazebo (gazebo_ros_pkg).](https://github.com/Math09/infnet_ros/tree/ros_noetic)
---

**Passo 1:** Atualizando pacotes ROS.

*Passo 1.1:* Atualizando Rosdep.
```bash
rosdep update
```

*Passo 1.2:* Atualizando pacotes do sistema.
```bash
sudo apt update
```

*Passo 1.3:* Atualização geral.
```bash
sudo apt dist-upgrade
```

**Passo 2:** Instalando o sistema de compilação ROS (catkin).
```bash
sudo apt install ros-noetic-catkin python3-catkin-tools
```


**Passo 3:** Instalando o wstool.
```bash
sudo apt install python3-wstool
```

**Passo 4:** Criando pasta 'ws_moveit'.
```bash
mkdir -p ~/ws_moveit/src
```

**Passo 5:** Entrando na pasta 'ws_moveit'.
```bash
cd ~/ws_moveit/src
```

**Passo 6:** Baixando fonte do MoveIt.

*Passo 6.1:* Inicializando wstool.
```bash
wstool init .
```

*Passo 6.2:* Fundindo wstool.
```bash
wstool merge -t . https://raw.githubusercontent.com/ros-planning/moveit/master/moveit.rosinstall
```

*Passo 6.3:* Removendo moveit_tutorials de wstool.
```bash
wstool remove  moveit_tutorials
```

*Passo 6.4:* Atualizando wstool.
```bash
wstool update -t.
```

**Passo 7:** Baixar código de exemplo.
```bash
git clone ros-planning/moveit_tutorials -b master
```

```bash
git clone ros-planning/panda_moveit_config -b melodic-devel
```

**Passo 8:** Build catkin workspace.
```bash
rosdep install -y --from-paths . --ignore-src --rosdistro noetic
```

```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros-testing/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

```bash
sudo apt update
```

```bash
cd ~/ws_moveit
```

```bash
catkin config --extend /opt/ros/noetic --cmake-args -DCMAKE_BUILD_TYPE=Release
```

```bash
catkin build
```
