# Instalando e configurando ROS-2 (Foxy).
A fim de instalar, configurar e executar o ROS-2 (Foxy), me fundamentei nos seguintes links:

* [Installing ROS 2 on Ubuntu Linux](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Binary.html)
* [ROS 2 Foxy Fitzroy - Patch Release 4](https://github.com/ros2/ros2/releases/tag/release-foxy-20201211)

Fluxograma para instalação do ROS-2 (Foxy). </br>
![flowchart install ros foxy](/images/flowchart_install_ros_foxy.png)

**Passo 1:** Instando pacotes necessários (curl | gnupg2 | lsb-release).
```bash
sudo apt update && sudo apt install curl gnupg2 lsb-release
```

**Passo 2:** Configurando chave.
```bash
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```

**Passo 3:** Adicionando repositório à lista de fontes.
```bash
sudo sh -c 'echo "deb [arch=$(dpkg --print-architecture)] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
```

**Passo 4:** Download ROS-2 (Foxy), baixar a versão compatível com o sistema operacional.
```
https://github.com/ros2/ros2/releases/tag/release-foxy-20201211
```

**Passo 5:** Extraindo instalador.
 -> Antes de extrair, mover o arquivo compactado para '/opt/ros'.
* Movendo arquivo.

Comando: 
```bash
sudo mv nome_do_arquivo /caminho_da_pasta
```

Exemplo: 
```bash
sudo mv ros2-foxy-20201211-linux-focal-amd64.tar.bz2 /opt/ros
```
* Extraindo arquivo.


Comando: 
```bash
sudo tar xf nome_do_arquivo
```

Exemplo: 
```bash
sudo tar xf ros2-foxy-20201211-linux-focal-amd64.tar.bz2
```

**Passo 6:** Configurando o caminho do ROS-2.

*Passo 6.1:* Abrindo o arquivo '.bashrc'.
```bash
sudo gedit .bashrc
```

*Passo 6.2:* Criando alias initros2.
```bash
alias initros2="source /opt/ros/ros2-linux/local_setup.bash";
```
 -> Após adicionar o alias salve e feche o arquivo '.bashrc'.

*Passo 6.3:* Atualizando '.bashrc'.
```bash
source .bashrc
```

**Passo 7:** Atualizando pacotes.
```bash
sudo apt update
```

**Passo 8:** Instalando pacote 'python3-rosdep'.
```bash
sudo apt install -y python3-rosdep
```

**Passo 9:** Configurando Rosdep.

*Passo 9.1:* Inicializando Rosdep.
```bash
sudo rosdep init
```

*Passo 9.2:* Atualizando Rosdep.
```bash
rosdep update
```

**Passo 10:** Instalando dependências ausentes.
 -> *AVISO: O caminho '/opt/ros/ros2-linux/share' varia dependendo de onde se põe o instalador do ROS-2.*
```bash
rosdep install --from-paths /opt/ros/ros2-linux/share --ignore-src --rosdistro foxy -y --skip-keys "console_bridge fastcdr fastrtps osrf_testing_tools_cpp poco_vendor rmw_connext_cpp rosidl_typesupport_connext_c rosidl_typesupport_connext_cpp rti-connext-dds-5.3.1 tinyxml_vendor tinyxml2_vendor urdfdom urdfdom_headers"
```

**Passo 11:** Instalando bibliotecas do python3.
```bash
sudo apt install -y libpython3-dev python3-pip
```

```bash
pip3 install -U argcomplete
```

---
Depois que terminar a instalação - ROS-2 (Foxy) - é necessário criar e configurar a pasta dev_ws. A fim de resolver isso criei o tutorial a seguir:

* [Criando e configurando workspace dev_ws.](https://github.com/Math09/infnet_ros/tree/dev_ws)
