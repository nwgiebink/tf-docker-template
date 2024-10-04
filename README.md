# tf-docker-template
Kickstart your Tensorflow docker environment with this example. The setup uses the tensorflow base image. [See more about integrating Tensorflow with Docker here](https://www.tensorflow.org/install/docker).

# Docker Prerequisites

[Install Docker](https://docs.docker.com/engine/install/) and follow these [important post-installation steps](https://docs.docker.com/engine/install/linux-postinstall/)

# NVIDIA Prerequisites

Check if a gpu is available on your device: `lspci | grep -i nvidia`

# Other Prerequisites

Make sure `make` is installed. 

```
sudo apt install make
```

## NVIDIA Drivers
The following example applies to an Ubuntu machine. Skip this step if NVIDIA drivers are already set up on your machine. 

1. Install the NVIDIA driver
Optionally check for the recommended version by running `ubuntu-drivers devices` (you may have to install ubuntu-drivers first).

Install the recommended NVIDIA driver version automatically via ubuntu-drivers
```
sudo ubuntu-drivers autoinstall
```
OR install a specific version
```
sudo apt install nvidia-driver-550
```

2. Reboot

To verify your installation, run `nvidia-smi`


## NVIDIA Container Toolkit
See the [NVIDIA Container Toolkit docs](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html) for more detail and alternative setup options. From the docs:

1. Configure the repository
```
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
  && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | \
    sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
    sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

2. Update packages and install
```
sudo apt-get update
```

```
sudo apt-get install -y nvidia-container-toolkit
```

3. Reboot 


Note: enable gpu when you run the docker container by including `--gpus all` in the `docker run` command. 
