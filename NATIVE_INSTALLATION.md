# Environment setup

Note: Native setup is not recommended for labs as if you have issues setting it up, we may not be able to resolve them.

## Install ROS
We will be using ROS Kinetic on Ubuntu 16.04 LTS (Xenial). **NO OTHER UBUNTU DISTRO/ROS VERSION IS SUPPORTED**

To install ROS Kinetic, follow the instructions here: [http://wiki.ros.org/kinetic/Installation/Ubuntu](http://wiki.ros.org/kinetic/Installation/Ubuntu)

Don't forget to edit your bashrc and install the development dependencies!

## Install Aikido dependencies
Add a few custom PPAs necessary for Aikido
```
$ sudo add-apt-repository ppa:dartsim/ppa
$ sudo add-apt-repository ppa:personalrobotics/ppa
$ sudo apt-get update
```

Install build dependencies for Dart
```
$ apt install git cmake build-essential libboost-filesystem-dev libmicrohttpd-dev libompl-dev libtinyxml2-dev libyaml-cpp-dev libccd-dev libfcl-dev liboctomap-dev libnlopt-dev liburdfdom-dev
```

Set your git identity. Substitute the email and name with the ones associated with your github account you use for the class.
```
$ git config --global user.email "tommy@usc.edu"
$ git config --global user.name "Tommy Trojan"
```

Build and install Dart from source
```
$ mkdir ~/ros_dependencies && cd ~/ros_dependencies
$ git clone https://github.com/dartsim/dart.git
$ cd dart
$ git checkout tags/v6.7.3
$ mkdir build && cd build
$ cmake ..
$ make -j4
$ make install
```

Extend your shared library path to include libdart
```
$ echo 'export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/lib"' >> ~/.bashrc
$ source ~/.bashrc
```

Install some miscellaneous dependencies
```
$ apt install ros-kinetic-controller-interface ros-kinetic-transmission-interface ros-kinetic-realtime-tools ros-kinetic-controller-manager ros-kinetic-control-toolbox ros-kinetic-octomap-ros ros-kinetic-srdfdom python-catkin-tools python-pybind11
```
