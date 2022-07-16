# install-ros
# install ros in ubuntu
-  Configure your Ubuntu repositories.

```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
-  Set up your keys
```bash
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
-  Installation
```bash
sudo apt update
```
-  Now pick how much of ROS you would like to install.
```bash
sudo apt install ros-noetic-desktop-full
```
-  Desktop Install: Everything in ROS-Base plus tools like rqt and rviz
```bash
sudo apt install ros-noetic-desktop
```
- ROS-Base: (Bare Bones) ROS packaging, build, and communication libraries. No GUI tools.
```bash
sudo apt install ros-noetic-ros-base
```
- There are even more packages available in ROS. You can always install a specific package directly.
```bash
sudo apt install ros-noetic-PACKAGE
```
- e.g.
```bash
sudo apt install ros-noetic-slam-gmapping
```
- Environment setup
```bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
-  if you use zsh
```bash
echo "source /opt/ros/noetic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```
- Dependencies for building packages
```bash
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```
-  Initialize rosdep
```bash
sudo apt install python3-rosdep
```
-  With the following, you can initialize rosdep.
```bash
sudo rosdep init
rosdep update
```

# instaii ros on jetson nano
# install xubuntu in Jetson Nano
https://github.com/Discombobulated88/Xubuntu-20.04-L4T-32.3.1/releases/download/v1.0/Xubuntu-20.04-l4t-r32.3.1.tar.tbz2
# download balena
https://www.balena.io/etcher/
# ros install
# Set locale
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```bash
locale  # check for UTF-8
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
locale  # verify settings
```
- Setup Sources
 ```bash
apt-cache policy | grep universe
```
- This should output a line like the one below:
```bash
500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
    release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=amd64
  ```
-  If you don’t see an output line like the one above, then enable the Universe repository with these instructions.
```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```
- Now add the ROS 2 apt repository to your system.
```bash
sudo apt update && sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg
```
-  Then add the repository to your sources list.
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```
# Install ROS packages
- Update your apt repository caches after setting up the repositories.
```bash
sudo apt update
```
- ROS packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages.
```bash
sudo apt upgrade
```
-  Desktop Install (Recommended): ROS, RViz, demos, tutorials.
```bash
sudo apt install ros-foxy-desktop
```
- ROS-Base Install (Bare Bones): Communication libraries, message packages, command line tools. No GUI tools.
```bash
sudo apt install ros-foxy-ros-base
```
# Environment setup
```bash
echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
- if you use zsh
```bash
echo "source /opt/ros/foxy/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```
# Try some examples
- In one terminal, source the setup file and then run a C++ talker:
```bash
ros2 run demo_nodes_cpp talker
```
- In another terminal source the setup file and then run a Python listener:
```bash
ros2 run demo_nodes_py listener
```
