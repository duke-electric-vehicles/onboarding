# Development Environment Overview:
Our autonomous system uses the [Robot Operating System](https://www.ros.org/) for data management and communication. ROS, however, is rather difficult to install and maintain locally. Instead, we use a [Docker](https://www.docker.com/) container running a preconfigured version of Ubuntu with ROS pre-installed. You can think of docker as a very lightweight version of a virtual machine.

# Two Main Options:
### 1. Docker on either Windows or Mac
This method just requires a quick download and a few commands.
### 2. Native Dual-Boot
This requires more disk space and dedication than the previous method but provides a clean / efficient environment. You will still be using Docker to test ROS packages but will be able to take full advantage of a customizable Linux environment with a variety of command line tools.

### Important: For both setups, you will be using docker to test your ROS code

## Instructions for Option 1:
**Windows 10 Home:** click [here](https://docs.docker.com/docker-for-windows/install-windows-home/). This will guide you through the installation process of docker. Since Windows 10 Home doesn't have hyper-v (a backend required for docker virtualization), this guide will walk you through installing the Windows Subsytem for Linux (WSL). This is a project developed by Microsoft to enable a linux terminal within Windows. This is NOT to be confused with the Docker terminal, which requires the WSL backend.

**For Windows 10 Pro:** click [here](https://docs.docker.com/docker-for-windows/install/). This is similar to the link above but will not install WSL, as Windows 10 Pro does have hyper-v.

**For Mac:** click [here](https://docs.docker.com/docker-for-mac/install/). MacOS doesn't have any issues with a virtualization backend. As long as you are on a recent version of macOS, you should be fine.

## Instructions for Option 2:
*TODO*


## Installing ROS into the Docker Container:
**Overview of Docker:** Docker allows you to run many different environments. Docker "images" are templates for creating Docker "containers." The usual Docker workflow consists of writing your code locally. Creating a docker container from a pre-existing image, and mounting your code into the container. Then, you can test your code with ROS and make edits. Once you are done with your testing session, you exit Docker and the container is automatically deleted (but your code is saved on your local machine).

**Getting the ROS Docker Image**
Start Docker (this will slightly vary depending on your environment), and run:
```
docker pull melodic-ros-core
```
This will download an Ubuntu environment with ROS installed. Once the command finishes, run
```
docker image list
```
You should see an entry corresponding to the ros image you just downloaded / installed. Note the name under the Repository column.

To start and enter the container, run
```
docker run -it <IMAGENAME>
```
Where <IMAGENAME> is the repository name you noted in the previous step. Your bash prompt should now change to reflect the docker container. It should show something like `root@...:/#`
  
Within the docker container, run
```
rosversion -d
```
This should ouput "melodic," the version of ROS we are using. You have now finished installing Docker and have a testing environment for ROS packages!
