# Implementing Docker in CentOS 8 Server

## Introduction
This guide covers the step-by-step process of implementing Docker on a CentOS 8 server. CentOS 8 is a Linux web server based on Red Hat.

## Prerequisites
- **Access to CentOS 8 Server:** You should have access to the server either locally or via a virtual machine.

## Step-by-Step Guide

1. **Download Docker onto the server using `curl`:**
    - **Command:** `sudo curl -fsSL https://download.docker.com/linux/centos/docker-ce.repo -o /etc/yum.repos.d/docker-ce.repo`
    - ![This command downloads the Docker repository file and saves it to the appropriate directory.]

2. **Update the cache:**
    - **Command:** `sudo yum makecache`
    - ![This updates the package manager cache to verify that the Docker repository was successfully added.]

3. **Install Docker (Community Edition):**
    - **Command:** `sudo dnf -y install docker-ce --nobest`
    - ![This installs Docker CE (Community Edition) with the `--nobest` flag to avoid potential dependency issues.]

4. **Enable and start Docker:**
    - **Command:** `sudo systemctl enable --now docker`
    - ![This command enables Docker to start on boot and starts the Docker service immediately.]

5. **Reboot the server:**
    - ![Reboot the server to ensure Docker starts on boot.]

6. **Check the Docker version:**
    - **Command:** `docker version`
    - ![This checks the installed version of Docker, confirming the installation was successful.]

7. **Add a user to the Docker group:**
    - **Command:** `sudo usermod -aG docker sampleUser`
    - ![This command adds the user `sampleUser` to the Docker group, allowing them to execute Docker commands without being root.]

8. **Verify the user's groups:**
    - **Command:** `id sampleUser`
    - ![This command displays the groups that the user `sampleUser` belongs to, confirming their membership in the Docker group.]

## Testing Docker

1. **Run a sample Docker image:**
    - **Command:** `docker run hello-world`
    - ![This runs the "hello-world" Docker image. If it's not available locally, it will be pulled from the Docker repository.]

2. **Search for Docker images:**
    - **Command:** `docker search ubuntu`
    - ![This returns all Docker images that contain "ubuntu" as the search term.]

3. **Search for other Docker images:**
    - **Command:** `docker search react`
    - ![This returns Docker images that contain "react" as the search term.]
    - **Command:** `docker search node`
    - ![This returns Docker images that contain "node" as the search term.]
    - **Command:** `docker search openHims`
    - ![This returns Docker images that contain "openHims" as the search term.]

4. **View Docker help:**
    - **Command:** `docker`
    - ![This command displays options and commands available with Docker.]
