# Development Environment Overview:
Our autonomous system uses the [Robot Operating System](https://www.ros.org/) for data management and communication. ROS, however, is rather difficult to install and maintain locally. Instead, we use a [Docker](https://www.docker.com/) container running a preconfigured version of Ubuntu with ROS pre-installed. You can think of docker as a very lightweight version of a virtual machine.

# Two Main Options:
### 1. Docker on either Windows or Mac
This method just requires a quick download and a few commands.
### 2. Native Dual-Boot
This requires more disk space and dedication than the previous method but provides a clean / efficient environment. You will still be using Docker to test ROS packages but will be able to take full advantage of a customizable Linux environment with a variety of command line tools. At least 40GB of free space is recommended if you choose this option.

### Important: For both setups, you will be using docker to test your ROS code

## Instructions for Option 1:
**Windows 10 Home:** click [here](https://docs.docker.com/docker-for-windows/install-windows-home/). This will guide you through the installation process of docker. Since Windows 10 Home doesn't have hyper-v (a backend required for docker virtualization), this guide will walk you through installing the Windows Subsytem for Linux (WSL). This is a project developed by Microsoft to enable a linux terminal within Windows. This is NOT to be confused with the Docker terminal, which requires the WSL backend.

**For Windows 10 Pro:** click [here](https://docs.docker.com/docker-for-windows/install/). This is similar to the link above but will not install WSL, as Windows 10 Pro does have hyper-v.

**For Mac:** click [here](https://docs.docker.com/docker-for-mac/install/). MacOS doesn't have any issues with a virtualization backend. As long as you are on a recent version of macOS, you should be fine.

## Instructions for Option 2:
**Note:** It is recommended that you create a Windows backup before proceeding in the rare event of data corruption. We are not responsible for any damage to your computer if the installation fails.

**Creating a Disk Partition:** In order to dual-boot from your computer, you first need to create a disk partition. A disk partition is an unallocated amount of space in your hard drive. You will be using this unallocated space to contain Ubuntu. The following instructions apply to Windows computers:
1. Go to Windows Start and search for "partition" and click on the first result.
2. On your main disk (generally Disk 0), hover over to your C: Disk and right click on it. Then selected "Shrink Volume"
3. In the field that says "Enter total amount of space to shrink by in MB", type in "40,000" and click shrink. This will create a new 40GB partition.
4. Save all of your changes and exit the window.

**Installing Ubuntu:** 
Windows: For instructions on installing Ubuntu on a Windows computer, go ahead and **carefully** follow the instructions in this link: https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/ 

MacOS: For installing Ubunutu on MacOS (Catalina or lower), follow along this link: https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733 

## Installing ROS into the Docker Container:
**Overview of Docker:** Docker allows you to run many different environments. Docker "images" are templates for creating Docker "containers." The usual Docker workflow consists of writing your code locally. Creating a docker container from a pre-existing image, and mounting your code into the container. Then, you can test your code with ROS and make edits. Once you are done with your testing session, you exit Docker and the container is automatically deleted (but your code is saved on your local machine).

**Getting the ROS Docker Image**
Start Docker (this will slightly vary depending on your environment), and run:
```
docker pull ros:melodic-ros-core
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
Where \<IMAGENAME\> is the repository name you noted in the previous step. Your bash prompt should now change to reflect the docker container. It should show something like `root@...:/#`
  
Within the docker container, run
```
rosversion -d
```
This should ouput "melodic," the version of ROS we are using. You have now finished installing Docker and have a testing environment for ROS packages!
