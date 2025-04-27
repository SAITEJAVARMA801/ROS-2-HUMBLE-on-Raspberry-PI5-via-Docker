# ROS-2-HUMBLE-on-Raspberry-PI5-via-Docker
Step-by-Step Instructions
1. Install docker
   # Update package list
   sudo apt update
   # Install Docker
   sudo apt install -y docker.io
   # Enable and start Docker service
   sudo systemctl enable docker
   sudo systemctl start docker
   # Restart your terminal or run:
   newgrp docker

2. Create a working directory
   mkdir ~/ros2_humble_docker
   cd ~/ros2_humble_docker

3. Create a Dockerfile
   nano Dockerfile

4. Paste the code from the docker.txt


5. Build the Docker Image
   docker build -t ros2-humble-arm64
   
6. Run the Docker Container
   xhost +local:docker


7. Run the Container
docker run -it \
    --rm \
    --net=host \
    --env="DISPLAY" \
    --env="QT_X11_NO_MITSHM=1" \
    --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
    ros2-humble-arm64

