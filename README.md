# install-ros2-foxy
ROS 2 Foxy Fitzroy is a Long-Term Support (LTS) release designed for Ubuntu 20.04. It provides enhanced performance, improved security, and real-time capabilities for robotics development. Foxy supports a wider range of platforms and promotes modular and scalable software design, making it ideal for both research and industrial applications.


### Set locale
```
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```
### Setup Sources
You will need to add the ROS 2 apt repository to your system.

1- First ensure that the Ubuntu Universe repository is enabled.

```
sudo apt install software-properties-common
sudo add-apt-repository universe
```
2-  add the ROS 2 GPG key with apt.

```
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```
3- add the repository to your sources list.
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

### Install ROS 2 packages
Update your apt repository caches after setting up the repositories.

```
sudo apt update
```
ROS 2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages.

```
sudo apt upgrade
```
Desktop Install (Recommended): ROS, RViz, demos, tutorials.

```
sudo apt install ros-foxy-desktop python3-argcomplete
```
### Environment setup 
Sourcing the setup script

Set up your environment by sourcing the following file.

```
# Replace ".bash" with your shell if you're not using bash
# Possible values are: setup.bash, setup.sh, setup.zsh
source /opt/ros/foxy/setup.bash
```

### Try some examples

Source the ROS 2 Foxy Setup File

Open a terminal and source the ROS 2 Foxy setup file:

```
source /opt/ros/foxy/setup.bash
```

Run a C++ Talker Node

In the same terminal, run the C++ talker node:

```
ros2 run demo_nodes_cpp talker
```

Run a Python Listener Node

Open another terminal, source the ROS 2 Foxy setup file, and run the Python listener node:

```
source /opt/ros/foxy/setup.bash
ros2 run demo_nodes_py listener

```
### Example Output

In the terminal running the talker node, you will see:
```
[INFO] [talker]: Publishing: 'Hello World: 1'
[INFO] [talker]: Publishing: 'Hello World: 2'

```
In the terminal running the listener node, you will see:

```
[INFO] [listener]: I heard: 'Hello World: 1'
[INFO] [listener]: I heard: 'Hello World: 2'
...

```
