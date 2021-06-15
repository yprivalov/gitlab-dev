# gitlab-dev
Deploy Gitlab-web and Gitlab-runner in one host. **Only for testing and development**


## Installation

Edit GITLAB_HOME=<path to gitlab> in .env file
  
docker-compose build
docker-compose up -d

mkdir $GITLAB_HOME/gitlab-runner/config/certs  
cp $GITLAB_HOME/gitlab/config/ssl/gitlab.local.key $GITLAB_HOME/gitlab-runner/config/certs/  
cp %GITLAB_HOME/gitlab/config/ssl/gitlab-web.crt $GITLAB_HOME/gitlab-runner/config/certs/  

## Runner registration  

Edit registration token in gitlab-runer-register.sh

![image](./uploads/runner.jpg)

chmod 755 gitlab-runer-register.sh  
./gitlab-runer-register.sh  


