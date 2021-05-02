# Instalando e configurando ROS-1 (Noetic) e Gazebo (gazebo_ros_pkg).
A fim de instalar, configurar e executar o ROS-1 (Noetic) e o Gazebo (gazebo_ros_pkg) me fundamentei nos seguintes links:

* [ROS-1 (Noetic) - Ubuntu install of ROS Noetic](http://wiki.ros.org/noetic/Installation/Ubuntu)
* [Gazebo (gazebo_ros_pkgs) - Installing gazebo_ros_pkgs (ROS 1)](http://gazebosim.org/tutorials?tut=ros_installing&cat=connect_ros)

Fluxograma para a instalação do ROS-1 (Noetic). </br>
![flowchart install ros noetic](/images/flowchart_install_ros_noetic.png)

## Instalando ROS-1 (Noetic).
**Passo 1:** Configurar o sources.list para aceitar a instalação.
```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

**Passo 2:** Configurando chave. <br/>
*Antes de realizar o comando para configurar a chave, é necessário verificar se o pacote **curl** está instalado no sistema.*

---
Verificando a versão do pacote curl:
```bash
curl --version
```
Caso apareça este retorno é necessário instalar o curl: <br/>
![curl not found](/images/ros-noetic/curl_not_found.png)

Porém caso apareça esse retorno no terminal pule a instalação do curl: <br/>
![curl version](/images/ros-noetic/curl_version.png)

Instalando o pacote curl:
```bash
sudo apt-get install curl
```
---

```bash
curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add -
```

**Passo 3:** Atualizando pacotes do sistema.
```bash
sudo apt update
```

**Passo 4:** Comando para instalar o ROS-1. <br/>
*Usar APENAS um dos comando a seguir.*

* Instalando ROS Desktop-Full (Instalação Completa).
```bash
sudo apt install ros-noetic-desktop-full
```

* Instalando ROS-Desktop.
```bash
sudo apt install ros-noetic-desktop
```

* Instalando ROS-Base.
```bash
sudo apt install ros-noetic-ros-base
```

**Passo 5:** Instalando dependências para construção de pacotes.
```bash
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```

**Passo 6:** Configurando Rosdep.

*Passo 6.1:* Inicializando Rosdep.
```bash
sudo rosdep init
```

*Passo 6.2:* Atualizando Rosdep.
```bash
rosdep update
```

**Passo 7:** Configurando o caminho do ROS-1.

*Passo 7.1:* Abrindo o arquivo '.bashrc'.
```bash
sudo gedit .bashrc
```

*Passo 7.2:* Criando o alias initros1.
(Adicionar esse caminho ao '.bashrc' - normalmente pode ser adicionado no final do arquivo)
```bash
alias initros1="source /opt/ros/noetic/setup.bash";
```
Após adicionar o alias salve e feche o arquivo '.bashrc'.

*Passo 7.3:* Atualizando '.bashrc'.
```bash
source .bashrc
```

### Após a instalação execute os comandos a seguir para atribuir e verificar a versão do ROS. <br/>
1. Comando para atribuir a versão do ROS.
```bash
initros1
```
2. Comando para verificar a versão do ROS.
```bash
rosversion -d
```
3. Assim o terminar deverá ficar da seguinte forma: <br/>
![ros version](/images/ros-noetic/ros_version.png)

---
## Verificando e Instalando o Gazebo (gazebo_ros_pkg).
Fluxograma para a verificação/instalação do Gazebo. </br>
![flowchart gazebo](/images/flowchart_gazebo.png)

**Passo 1:** Verificando se o gazebo foi instalado. <br/>
Existem algumas maneiras de verificar se o Gazebo foi instalado na máquina.

1. O ícone deve estar no menu do sistema. <br/>
*Se o gazebo foi instalado junto com o ROS-1 possívelmente apareceram esses ícones, caso apareça apenas o ícone do Gazebo é oportuno realizar os outros testes.* <br/>
![gazebo icons](/images/gazebo/gazebo_icon.png)

2. Verificar a versão do Gazebo, no terminal.
```bash
gazebo --version
```
Possíveis retornos: <br/>
```if( Se estiver instalado, esse será o retorno ):``` <br/>
![gazebo version](/images/gazebo/gazebo_version.png)

```else( Caso não esteja ):``` <br/>
![gazebo version not found](/images/gazebo/gazebo_version_not_found.png)

3. Verificar se as pastas '/gzserver' e '/gzclient' estão instaladas, no terminal. 
```bash
which gzserver && which gzclient
```
Possiveis retornos: <br/>
```if( Se estiver instalado, esse será o retorno ):``` <br/>
![gazebo folder](/images/gazebo/gazebo_folder.png)

```else( Caso não esteja ):``` <br/>
![gazebo folder not found](/images/gazebo/gazebo_folder_not_found.png)

4. Tentar executar o comando para abrir o gazebo, no terminal.
```bash
gazebo
```
Possíveis retornos: <br/>
```if( Se estiver instalado, esse será o retorno ):``` <br/>
![gazebo open](/images/gazebo/gazebo.png) <br/>
![gazebo terminal](/images/gazebo/gazebo_terminal.png)

```else( Caso não esteja ):``` <br/>
![gazebo not found](/images/gazebo/gazebo_not_found.png)

**Passo 2:** Instalando o Gazebo (gazebo_ros_pkg).

*Passo 2.1:* Instalando Debians pré construídos.
```bash
sudo apt-get install ros-noetic-gazebo-ros-pkgs ros-noetic-gazebo-ros-control
```
* Onde está a palavra noetic pode ser substituída por qualquer versão, tais como:
    * ROS - Lunar
    * ROS - Kinetic
    * ROS - Indigo

*Passo 2.2:* Instalando o Gazebo
```bash
sudo apt-get install -y libgazebo11-dev
```
Após terminar a instalação volte ao **passo 1** para verificar se o Gazebo foi instalado corretamente.

---
Depois que terminar todas as instalações - ROS-1 (Noetic) e Gazebo (gazebo_ros_pkg) - é necessário criar e configurar a pasta catkin_ws. A fim de resolver isso criei o tutorial a seguir:

* [Criando e configurando pasta catkin_ws](https://github.com/Math09/infnet_ros/tree/creating_catkin_ws_folder)
