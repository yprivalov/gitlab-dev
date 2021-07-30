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


# How to reset your root password
To reset your root password, first log into your server with root privileges.

Start a Ruby on Rails console with this command:

```gitlab-rails console -e production```

Wait until the console has loaded.

There are multiple ways to find your user. You can search for email or username.

```user = User.where(id: 1).first```
or
```user = User.find_by(email: 'admin@example.com')```

Now you can change your password:
```
user.password = 'secret_pass'
user.password_confirmation = 'secret_pass'
```
It’s important that you change both password and password_confirmation to make it work.

Don’t forget to save the changes.
```user.save!  
  user.unlock_access!
  ```
  
# Certificate
https://forum.gitlab.com/t/using-a-self-signed-certificate/1111/4
