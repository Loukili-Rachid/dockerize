FROM jenkins/jenkins:lts

USER root
RUN apt-get update && apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common \
    && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
    && add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/debian \
       $(lsb_release -cs) \
       stable" \
    && apt-get update && apt-get install -y docker-ce

RUN usermod -aG docker jenkins
COPY .docker/jenkins/jenkins_home/ /var/jenkins_home/
#RUN chown -R jenkins:jenkins /var/jenkins_home/caches
#RUN chmod -R 755 /var/jenkins_home/caches/*

CMD ["chmod", "+x", "/var/jenkins_home/caches/" , "&&", "chmod", "+x", "/var/jenkins_home/caches/*"]