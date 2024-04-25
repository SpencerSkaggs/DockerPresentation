# Docker Guide for Local Hosting and CentOS 8 Server Setup

## What is Docker?

Docker is a platform for building and running applications into standardized units called containers. These containers are mostly isolated from the rest of the system (server) and contain everything they need to run self-contained.

In the context of web development, Docker allows us to deploy an application on any server without having to worry about installing other dependencies or encountering conflicts with other applications on the same server.

## How Does Docker Work?

Docker provides a standardized way to run our code. Docker itself is an operating system for containers, similar to how virtual machines (VMs) virtualize server hardware. Docker virtualizes an operating system for a server and is used to build, run, start, and stop containers.

## Why Use Docker?

Docker provides several benefits in development:

- **Improved server resource allocation:** Docker allows us to run more code on our servers, reducing costs.
- **Seamless deployment:** Moving applications from the local machine to production is streamlined, eliminating the common issue of “it runs on my machine.”

## Local Docker

In this example, we will use a locally hosted sample project built in Node.js and React, running the project through Docker Desktop.

1. **Clone the application from GitHub:**
    - **Command:** `git clone https://github.com/docker/getting-started-app.git`
    - The directory should look like this:

    ```
    ├── getting-started-app/
        ├── package.json
        ├── README.md
        ├── spec/
        ├── src/
        └── yarn.lock
    ```

2. **Build the Docker Image with a Dockerfile:**
    - A Dockerfile is a text file that contains a script of instructions for building a container image.

    ```Dockerfile
    FROM node:18-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "src/index.js"]
    EXPOSE 3000
    ```

    - **Command:** `docker build -t getting-started .`
    - `-t` is a tag flag for the image, giving it the name “getting-started.”
    - `.` at the end of the command tells Docker to look for the Dockerfile in the current directory.

3. **Run the Docker Image:**
    - **Command:** `docker run -dp 127.0.0.1:3000:3000 getting-started`
    - Open a web browser and visit `http://127.0.0.1:3000` to see the sample app.

By following these steps, you can create a fully functional local environment with frontend and backend communication and a persistent database, all without having to download React, Node.js, or other dependencies.

## Step-by-Step Guide to Implement DockerRepository in CentOS 8 Server

1. **Access the Linux server using a virtual machine (for example).**

2. **Check for package updates (if required):**
    - **Command:** `sudo dnf check-update`
    - If updates are available, use the following command:
    - **Command:** `sudo dnf upgrade`

3. **Download Docker onto the server using `curl`:**
    - **Command:** `sudo curl https://download.docker.com/linux/centos/docker-ce.repo -o /etc/yum.repos.d/docker-ce.repo`

4. **Update the cache:**
    - **Command:** `sudo yum makecache`

5. **Install Docker on the CentOS 8 server (Community Edition):**
    - **Command:** `sudo dnf -y install docker-ce --nobest`

6. **Enable Docker Daemon:**
    - **Command:** `sudo systemctl enable --now docker`

7. **Reboot the server and check Docker version for testing:**
    - **Command:** `docker version`

8. **Add a user to the Docker group:**
    - **Command:** `sudo usermod -aG docker sampleUser`
    - Verify the user's groups:
    - **Command:** `id sampleUser`

At this point, Docker is downloaded, installed, and configured for the user to use Docker.

## Testing Docker

1. **Run a sample Docker image provided by Docker:**
    - **Command:** `docker run hello-world`
    - This will pull the image from the Docker repository if it isn't already local.

2. **View Docker help options and commands:**
    - **Command:** `docker`

## Download an Image and Set Up a Container

1. **Search for Docker images:**
    - **Command:** `docker search ubuntu`
    - This returns all Docker images that contain "ubuntu."

2. **Search for other Docker images:**
    - **Command:** `docker search react`
    - **Command:** `docker search node`
    - **Command:** `docker search openHims`
    - Use these commands to search for Docker images of interest.
