FROM jenkins/jenkins:2.289.3-lts-jdk11
USER root
ENV http_proxy=http://proxy.company.com:8080 \
    https_proxy=https://proxy.company.com:443 \
    no_proxy=127.0.0.1,localhost,company.com
RUN apt-get update && apt-get install -y apt-transport-https \
       ca-certificates curl gnupg2 \
       software-properties-common
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN apt-key fingerprint 0EBFCD88
RUN add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/debian \
       $(lsb_release -cs) stable"
RUN apt-get update && apt-get install -y docker-ce-cli
RUN usermod -aG docker jenkins 
RUN setfacl -m user:$USER:rwx /var/run/docker.sock


#sudo docker run -d -v jenkins_home:/var/jenkins_home \
   # -p 8080:8080 -p 50000:50000 \
    # -v /var/run/docker.sock:/var/run/docker.sock customjenkins
 #  usermod -aG docker jenkins 
