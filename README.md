# Criando e configurando workspace catkin_ws.

Com a finalidade de criar e configurar a pasta catkin_ws me fundamentei no link:
* [BuildingPackages](http://wiki.ros.org/noetic/Installation/Ubuntu)

Fluxograma para a criação/configuração da pasta catkin_ws.
![flowchart create folder](/images/flowchart_create_folder.png)

**Passo 1:** Executando o comando para atribuir a versão noetic.
```bash
initros1
```

Verificando a versão atribuída:
```bash
rosversion -d
```

Assim deverá ser o retono, no terminal: <br/>
![ros version](/images/ros_version.png)

**Passo 2:** Criando pasta que será o pacote para o ROS-1. <br/>
 -> *Normalmente a workspace catkin_ws é criada na Pasta Pessoal do usuário, '/home/[nome_do_usuario]/', ou dentro de uma outra pasta workspace (também na Pasta Pessoal), caso se utilize mais de uma versão do ROS.*
```bash
mkdir -p ~/catkin_ws/src
```

**Passo 3:** Entrando na pasta 'catkin_ws/src'.
```bash
cd ~/catkin_ws/src
```

**Passo 4:** Iniciando workspace.
```bash
catkin_init_workspace
```

Ocorrendo esse retorno, no terminal: <br/>
![init workspace](/images/init_workspace.png)

 -> **Desta forma é gerado o arquivo 'CMakeLists.txt'.**

**Passo 5:** Retornando para a pasta raiz do catkin_ws. <br/>
 -> *Usar APENAS um dos comandos a seguir:* <- <br/>
```bash
cd ~/catkin_ws/
```

Ou pode usar esse comando alternativo:
```bash
cd ..
```

**Passo 6:** Executando o comando que adiciona utilidades ao fluxo de trabalho do padrão catkin.
```bash
catkin_make
```
Retorno no terminal:
```bash
Base path: /home/user/catkin_ws
Source space: /home/user/catkin_ws/src
Build space: /home/user/catkin_ws/build
Devel space: /home/user/catkin_ws/devel
Install space: /home/user/catkin_ws/install
####
#### Running command: "cmake /home/user/catkin_ws/src -DCATKIN_DEVEL_PREFIX=/home/user/catkin_ws/devel -DCMAKE_INSTALL_PREFIX=/home/user/catkin_ws/install -G Unix Makefiles" in "/home/user/catkin_ws/build"
####
-- The C compiler identification is GNU 9.3.0
-- The CXX compiler identification is GNU 9.3.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Using CATKIN_DEVEL_PREFIX: /home/user/catkin_ws/devel
-- Using CMAKE_PREFIX_PATH: /opt/ros/noetic
-- This workspace overlays: /opt/ros/noetic
-- Found PythonInterp: /usr/bin/python3 (found suitable version "3.8.5", minimum required is "3") 
-- Using PYTHON_EXECUTABLE: /usr/bin/python3
-- Using Debian Python package layout
-- Found PY_em: /usr/lib/python3/dist-packages/em.py  
-- Using empy: /usr/lib/python3/dist-packages/em.py
-- Using CATKIN_ENABLE_TESTING: ON
-- Call enable_testing()
-- Using CATKIN_TEST_RESULTS_DIR: /home/user/catkin_ws/build/test_results
-- Forcing gtest/gmock from source, though one was otherwise available.
-- Found gtest sources under '/usr/src/googletest': gtests will be built
-- Found gmock sources under '/usr/src/googletest': gmock will be built
-- Found PythonInterp: /usr/bin/python3 (found version "3.8.5") 
-- Found Threads: TRUE  
-- Using Python nosetests: /usr/bin/nosetests3
-- catkin 0.8.9
-- BUILD_SHARED_LIBS is on
-- BUILD_SHARED_LIBS is on
-- Configuring done
-- Generating done
-- Build files have been written to: /home/user/catkin_ws/build
####
#### Running command: "make -j2 -l2" in "/home/user/catkin_ws/build"
####
```
Após executar o comando são geradas duas pastas: 
* build
* devel

![folders](/images/folders.png)

**Passo 7:** Adicionando o caminho do catkin ao alias 'initros1'.

*Passo 7.1:* Retornando a pasta raiz do Ubuntu.
```bash
cd
```

*Passo 7.2:* Abrindo o arquivo '.bashrc'.
```bash
sudo gedit .bashrc
```

*Passo 7.3:* Adicionando o seguinte caminho ao alias do 'initros1'.
```bash
source ~/catkin_ws/devel/setup.bash
```

Assim deverá ficar o alias com os dois caminhos:
```bash
alias initros1="source /opt/ros/noetic/setup.bash && source ~/catkin_ws/devel/setup.bash";
```

-> Após adicionar o alias salve e feche o arquivo '.bashrc'.

*Passo 7.4:* Atualizando .bashrc.
```bash
source .bashrc
```

---
Caso a criação e nem a configuração do workspace catkin_ws funcione, pode ser que não esteja com o ROS-1 (Noetic) instalado. Para isso volte para o tutorial:
* [Instalando e configurando ROS-1 (Noetic) e Gazebo (gazebo_ros_pkg).](https://github.com/Math09/infnet_ros/tree/ros_noetic)
