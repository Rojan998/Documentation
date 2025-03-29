# Welcome to Jenkins Installation Guide

## Java17 Installation

Make a `.sh` file and paste the code below

    sudo apt update -y
    sudo apt install fontconfig openjdk-17-jre -y

<br>

    java --version

## Install Jenkins LTS

Make a `.sh` file and paste the code below

    sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
    https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
    echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null
    sudo apt-get update -y
    sudo apt-get install jenkins -y

## Enable Jenkins

    sudo systemctl enable jenkins

## Start Jenkins

    sudo systemctl start jenkins

## Check Status

    sudo systemctl status jenkins

## Browse Jenkins

Browse to `http://localhost:8080` (or whichever port you configured for Jenkins when installing it) and wait until the Unlock Jenkins page appears.
