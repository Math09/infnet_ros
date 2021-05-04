# Criando e configurando workspace dev_ws.
Com a finalidade de criar e configurar a pasta dev_ws me fundamentei no link:

* [ROS-2 (Foxy)](https://lms.infnet.edu.br/moodle/pluginfile.php/770517/mod_resource/content/1/7.Comunicacao%20em%20ROS2.pdf)

Fluxograma para a criação da pasta dev_ws. <br/>
![flowchart create folder]()

**Passo 1:** Executando o comando para atribuir a versão foxy.
```bash
initros2
```

Verificando a versão atribuída:
```bash
rosversion -d
```

Assim deverá ser o retorno, no terminal: <br/>
![ros version]()

No print aparece o warning, pois existem duas versões do ROS em uma mesma pasta - /opt/ros:
```bash
[connext_cmake_module] Warning: The location at which Connext was found when the workspace was built [[/opt/rti.com/rti_connext_dds-5.3.1]] does not point to a valid directory, and the NDDSHOME environment variable has not been set. Support for Connext will not be available.
```

**Passo 2:** Instalando compilador Colcon.
```bash
sudo apt install python3-colcon-common-extensions
```

**Passo 3:** Criando pasta que será o pacote ROS-2.
```bash
mkdir -p ~/dev_ws/src
```

**Passo 4:** Entrando na pasta '/dev_ws/src'.
```bash
cd ~/dev_ws
```

**Passo 5:** Verificando dependências.
```bash
rosdep install -i --from-path src --rosdistro foxy -y
```

Saída no terminal:
```bash
#All required rosdeps installed successfully
```

**Passo 6:** Criando espaço de trabalho.
```bash
colcon build --symlink-install
```

**Passo 7:** Compilando.
```bash
colcon build
```

**Passo 8:** Adicionando caminho da pasta dev_ws ao alias 'initros2'.

*Passo 8.1:* Retornando a pasta raiz do Ubuntu.
```bash
cd
```

*Passo 8.2:* Abrindo o arquivo '.bashrc'
```bash
sudo gedit .bashrc
```

*Passo 8.3:* Adicionando o seguinte caminho ao alias do 'initros2'.
```bash
source ~/dev_ws/install/local_setup.bash
```

Assim deverá ficar o alias com os dois caminhos:
```bash
 alias initros2="source /opt/ros/ros2-linux/local_setup.bash && source ~/dev_ws/install/local_setup.bash"
```

-> Após adicionar o alias salve e feche o arquivo '.bashrc'.

*Passo 8.4:* Atualizando .bashrc.
```bash
source .bashrc
```

---
Antes de criar e configurar o workspace dev_ws é necessário instalar o ROS-2 (Foxy), para isso volte ao tutorial:
* [Instalando e configurando ROS-2 (Foxy)](https://github.com/Math09/infnet_ros/tree/ros_foxy)
