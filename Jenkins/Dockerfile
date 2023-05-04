FROM jenkins/jenkins:2.387.3

USER root

# Update the apt package index and install packages to allow apt to use a repository over HTTPS:
RUN apt-get update
RUN apt-get -y install \
ca-certificates \
curl \
gnupg

# Add Docker’s official GPG key:
RUN install -m 0755 -d /etc/apt/keyrings
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
RUN chmod a+r /etc/apt/keyrings/docker.gpg
# Use the following command to set up the repository:
RUN echo \
"deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
"$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
tee /etc/apt/sources.list.d/docker.list > /dev/null
# Update the apt package index and install the latest version of docker
RUN apt-get update
RUN apt-get -y install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

RUN usermod -aG root jenkins
RUN usermod -aG docker jenkins