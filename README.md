# ROS-2-HUMBLE-on-Raspberry-Pi5-via-Docker
Step-by-step instructions to install ROS 2 Humble on a Raspberry Pi running Ubuntu 24.04 via Docker.

1. Install docker

Update package list
  
    sudo apt update
  Install Docker
  
   	sudo apt install -y docker.io
  Enable and start Docker service
  
 	  sudo systemctl enable docker
 	  sudo systemctl start docker
Restart your pi or run:

        newgrp docker
	
2. Create a working directory

       mkdir ~/ros2_humble_docker
   	   cd ~/ros2_humble_docker

3. Create a Dockerfile

       nano Dockerfile

4. Paste the code from the docker.txt
	
   Adjust the local time in the code according to your requirements

5. Build the Docker Image

       docker build -t ros2-humble-arm64
   
6. Run the Docker Container

        xhost +local:docker


7. Run the Container to start ros in docker

        docker run -it \
            --rm \
  	        --net=host \
  	        --env="DISPLAY" \
  	        --env="QT_X11_NO_MITSHM=1" \
  	        --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
            ros2-humble-arm64

8. Verify ROS 2 is installed

       source /opt/ros/humble/setup.bash
 	      ros2 topic list
          ros2 node list


