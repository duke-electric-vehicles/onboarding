# Overview of Publishers and Subscribers
In ROS, data communication occurs through topics. A topic is a data bus where nodes exchange messages (data). A publisher is a node that sends data (publishes) to a topic while a subscriber reads data from a topic.

Note: Topics are automatically created when a publisher publishes data to a topic that doesn't exist yet.

# Mounting Code into Docker Container
You can think of mounting code as plugging in a usb drive to your computer. When code is mounted into a docker container, all changes within that folder are saved. To mount code, you must specify a source and destination folder. The source folder is the local folder with all of your DEV code and the destination folder is where you want the code to be on the docker container. This should be ‘/root’.

In order to make this process easy, we will be using Docker-Compose. This service makes starting / stopping the docker container much easier (and will also automatically mount your code once it is set up).

# Docker Compose
First, if you haven’t already, create a folder on your local machine that will contain all of your code for DEV. Now, enter this folder and create a new file called docker-compose.yml. This file is known as a Docker Compose YAML file, which contains all of your container settings (mounting code, privileges, image version, etc). Now, open this file and add the following code:
```
version: "3.3"
services:
        dev:
                volumes:
                      - type: bind
                        source: <YOUR SOURCE FOLDER>
                        target: /root
                image: <YOUR ROS IMAGE>
                tty: true
                container_name: "dev"
                privileged: true
```
For the source, paste in the full path to your local source folder. This should be the folder you are within right now. For the ROS image, this should be in the format IMAGE_NAME:TAG. Now, save this file and return to your main DEV folder.

After [Installing Docker Compose](https://docs.docker.com/compose/install/), you should be able to run the following command from your DEV directory.
```
docker-compose up -d
```
This will start up your container in the background and mount your code to the /root directory in the container. Now, enter your container with the following command.
```
docker exec -it dev /bin/bash
```
Then, navigate to the /root directory. You should see any files / folders that were on your local machine here. Anything you create or edit in this folder will be automatically saved to your corresponding local folder. Even after the container is shut down.

Since you ran this container with docker compose, it will not immediately shut down when you exit. Instead, you need to run
```
docker-compose down
```
This will stop the container.

Now, you should be ready to move on to writing a pub / sub. Make sure all of your catkin packages are saved within the /root folder when working on the docker container.

# Writing a Pub / Sub
[Publisher Subscriber Tutorial](http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28python%29)

# Running the Pub / Sub
[Running the Publisher / Subscriber](http://wiki.ros.org/ROS/Tutorials/ExaminingPublisherSubscriber)

# Extension Task
Currently, your pub / sub is communicating with string messages. For the electric vehicle, we will mostly work with location and orientation data. Research the ROS “Twist” message and change your pub / sub to use Twist messages instead of strings.
