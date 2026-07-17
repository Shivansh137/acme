FROM jenkins/jenkins:lts

USER root

RUN apt-get update && \
    apt-get install -y docker.io

# Change the docker group ID to match the host
RUN groupmod -g 986 docker

# Add Jenkins user to docker group
RUN usermod -aG docker jenkins

USER jenkins