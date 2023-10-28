# Is there a Public SSH Key configured for the user called mike?
Click on the user called mike inside the People tab.

Next, click on Configure and inspect if a SSH Key has been added for this user.

# There is a SSH key-pair created under /home/mike/.ssh.


What is name of the public key?

![Screenshot from 2023-10-28 12-35-23](https://github.com/Althaf-official/KodeKloud_Jenkins/assets/105126131/1cb16e9c-bd42-4471-8b4f-abc924626869)

# Now add this public key (/home/mike/.ssh/jenkins_key.pub) in Jenkins for the user called mike. This will allow us to interact with Jenkins using the CLI.

To do this, copy the public key to the clipboard.

mike@jenkins-server:~$ cat .ssh/jenkins_key.pub 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQClraYlzfxuFDiL1a+7njJlrap6kzvFhWNQ4PYVQfCzfUvED6WPGXCu3ZAqMqpOLHEQkBa+hPuB+0VPZ4GMCjyxzR9YbqgxHQV44KdEUTv52KqZa5xpH0kR0CslGzXrJfEyOjx+rG/JIq0Pj0MtgnIoclqpIoa9Vdg0yUtiioqpoKcI73nbVhxd24auUKhz+LXngzuhSwEU1Dd7NuVVfiDjh4vxjVJYfIlhxQ9gYMUwiFsQsavyLPDQF9Q5/r/wS+YIMaOTmWcSdh4Cw8zQNDJ3vvHr0xdqfua9WMo/JodAEH4w0FfHcBJbz7dZA3WLsEF/aV+TBs6bFzE/FRwJkMlAfUGzbqt/Xf/JlCxc81yssZS+dQ4BkyQ07NuBdB3tES27It6LqR3P1j311NF5ZMU4kqjjCPfam3KnHxRw51BV7PWYh1M+MS3uxLhuY4SLniOpucJwKajuzDJkKbWRg63aj7BO8OUhVQMiuWSnRt473c7LRW5NaUhHdAyvbyw6vFs= mike@jenkins-server
mike@jenkins-server:~$ 
Next, add this key for the user (Navigate to People --> mike --> Configure --> SSH Public Keys)

Paste the key and hit Save.

![Screenshot from 2023-10-28 12-39-11](https://github.com/Althaf-official/KodeKloud_Jenkins/assets/105126131/7bbc9f42-b69a-4f5f-8da5-471068071763)


# We have configured the SSH service in Jenkins to listen on a fixed port. To find out the port in use, run the command below:

curl -Lv http://localhost:8085/login 2>&1 | grep -i 'x-ssh-endpoint'

Which port does the Jenkins SSH service use?


You can also check the port used by navigating to Dashboard ---> Manage Jenkins --> Security --> SSH Server


# Now that we have the port used by the Jenkins SSH server, let us begin interacting with Jenkins over ssh with the user mike.

As mike, try running the following commands:

mike@jenkins-server:~$ ssh -i /home/mike/.ssh/jenkins_key -l mike -p 8022 jenkins-server help

Keep a note of the options used with the SSH command:

-i flag is used to point to mike's private SSH key. Remember, we have already added the public key in the Jenkins configuration.
-l is the login user which in our example is mike
-p is the port which we found out in the previous step to be 8022

# Using the help command, find out the built-in command to safely restart Jenkins from the CLI.

ssh -i /home/mike/.ssh/jenkins_key -l mike -p 8022 jenkins-server  safe-restart






