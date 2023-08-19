<h2><b>Docker Notes for setup</b></h2>

<b> Pre Setup Summary</b><br>
<br>
•	Install an engine. <br>
•	Install Docker engine from the Docker website.  <br>
•	https://docs.docker.com/engine/install/ubuntu/

<br><b> Notes </b><br><br>
•	Docker manages containers.  Docker engine runs the containers.
•	Docker is open source.  
•	Docker engine is a daemon.  
•	There are many images available online.  
•	You can create networks, data volumes, and images that are managed by the docker daemon and cli.   
•	Containers are secure and lightweight. They do not need entire operating systems.     
•	Processes must match the underlying operating system.  
•	Docker desktop allows Linux VM to be used on windows.  

<br><b> Setup Summary </b><br><br>
•	Create an EC2 instance (Linux).  
•	Remove all old versions of Docker if installing on a new machine.  
•	Install docker on the EC2. Use commands from Docker website.  

<h2>Install Docker on Ubuntu</h2><br>
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
•	Only the root user can connect to Docker Daemon by default.  
•	You have to add others to the docker group.  
•	Edit group at /etc/group.  
•	Or use  usermod -aG docker ubuntu.  
•	Configure Ubuntu to start on boot:: sudo systemctl enable docker.  
•	Test with docker run hello-world.  This will test the creation of the image, it will find the image from the docker hub.  
•	Verify with docker ps -a


<h2>Extra Notes :</h2>
•	https://hub.docker.com/ stores images for Docker. <br>
• Docker hub is registry. <br>
•	A docker image is a stopped container that is archived that can have multiple layers.  <br>
•	App are with the images and containers run from the images.   <br>
•	Images are repositories in registries.  <br>
•	Amazon ECR, GCR are other registries.  Nexus 3, DTR, and jfrog antifactory are other registries that can be used.  <br>
•	Image layers are read only.  The container is a read/write layer.  <br>
•	To create an image, you use ‘docker run’. It will create a container from the image. You state the image in the command.  

