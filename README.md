# Home Assistant with Timescaledb and Grafana

## About the project
Building a docker enviroment for smart house. I use a Raspberry Pi 4, but anything that runs docker-compose can be used.

### Containers

* home-assistant
* timescaledb
* pgadmin4
* grafana
* mosquitto

## Getting Started

To get the project up and running on a Raspberry Pi 4 follow these simple steps. 

### Prerequisites

* Raspberry Pie OS
* SSH connection enabled

### Installing docker and docker compose

1. #### Update and upgrade. 
    Make shure the package manager has the latest version.

    ```sh
    sudo apt update && sudo apt upgrade && sudo apt autoremove && sudo apt autoclean
    ```
2. #### Install docker. 
    Docker provides a handy script for installing.

    ```sh
    curl -sSL https://get.docker.com | sh
    ```
3. #### Add a non-root user to the docker group.
    Docker by default only root users can run containers. To avoid having to use `sudo` with every docker command, add the current user to the docker group.

    ```sh
    sudo usermod -aG docker ${USER}
    ```
4. #### Install docker-compose.
    Installing docker-compose will can be done using pip3. To do that some packages needs to be installed.

    ```sh
    sudo apt-get install libffi-dev libssl-dev
    sudo apt install python3-dev
    sudo apt-get install -y python3 python3-pip
    ```
    After that pip3 can be used to install docker-compose.

    ```sh
    sudo pip3 install docker-compose
    ```
5. #### Enable dockersystem service to start on boot.
    This step is usefull when containers have a [restart policy](https://docs.docker.com/config/containers/start-containers-automatically/) set to `always` or `unless-stopped`. To make docker automatically start on boot run the following command.
    
    ```sh
    sudo systemctl enable docker
    ```