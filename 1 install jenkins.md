# Now let us install Jenkins on the centos-host machine and configure it to run on port 8090 instead of the default port 8080.


You can refer to the Jenkins Installation Docs located above the terminal.


Execute below given commands one by one:

```ruby
sudo yum install epel-release -y
sudo yum install java-11-openjdk -y
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo --no-check-certificate
sudo rpm --import http://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum install jenkins -y
```


Edit `/lib/systemd/system/jenkins.service` file and change Jenkins port to 8090 by updating `Environment="JENKINS_PORT="` variable value.


`sudo vi /lib/systemd/system/jenkins.service`



It should look like this:


`Environment="JENKINS_PORT=8090"`



Once done start Jenkins service.

`sudo systemctl start jenkins`



# Now, you should be able to access Jenkins using Jenkins button on the top bar. Complete its installation from UI and make sure to create first admin user as per details mentioned below:


Username: admin

Password: Admin321

Full name: Admin User

E-mail address: admin@example.com

1. You will find the Jenkins initial admin password in `/var/lib/jenkins/secrets/initialAdminPassword` file.

2. Under Customize Jenkins, select install suggested plugins option.




1. Under Create First Admin User, enter the required details as given in the question.

2. Then click on Save and Continue.

3. Under Instance Configuration, you can click on Not now.

4. Finally click on Start using Jenkins button.

