# Among the following options, which one is true with respect to the Jenkins build agent?


D. A build agent is typically a machine, or container, which connects to a Jenkins controller and executes tasks when directed by the controller.

# Can we use a docker container as an agent node for a Jenkins server?
Yes, we can use a docker container as well, as an agent node for a Jenkins server.


# Which of the followings is a pre-requisite for a Jenkins agent node?

java

# Can we use a Windows based machine as an agent node for a Jenkins server?

yes


# Install SSH Build Agents Jenkins plugin.

Login into the Jenkins server and follow the below given steps:

1. Go to Manage Jenkins.
2. Click on Plugins.
3. Under Available, search for SSH Build Agents plugin.
4. Select it and install.
5. Once installed click on Restart Jenkins when installation is complete and no jobs are running.
   ![image](https://github.com/Althaf-official/KodeKloud_Jenkins/assets/105126131/c6ba0f47-c862-4560-8fec-2f9f087c0ad1)


# Create a username and password based credentials in Jenkins as per details mentioned below:


Username: bob

Password: caleston123

Login into the Jenkins server and follow the below given steps:

1. Go to Manage Jenkins.
2. Click on Credentials.
3. Click on (global) under Domains.
4. From the option on the right side, click on Add Credentials.
5. Enter bob under Username.
6. Enter caleston123 under Password.

7. Leave other options as it is and click on OK.

# We have a centOS based host node01, which we want to use as a Jenkins agent node.
But before adding it to Jenkins as a node, we need to install some required dependencies on it.


You can SSH into node01 from Jenkins server using below given credentials:


Host Name: node01

Username: bob

Password: caleston123


Use below given command to SSH:

ssh bob@node01



Please install the required dependencies on this host, also make sure to install the dependencies which are compatible with the installed Jenkins version.

SSH into node01 host using below given command:

ssh bob@node01



Once logged in, run below given command to install java:

sudo yum install java-11 -y
![image](https://github.com/Althaf-official/KodeKloud_Jenkins/assets/105126131/7028dfb2-2b27-41da-9120-9e084d64eb4d)


Move back to Jenkins host:

exit



# Create a Permanent Agent type agent node named linux-node as per details mentioned below:


1. It should be launched via SSH.

2. You can use the credentials you created in the previous question.

3. The Host value should be node01

4. Its remote root directory should be /home/bob

5. Label it as node01

6. Make sure Only build jobs with label expressions matching this node option is selected for Usage.


Note: Just in case the node is in error state after creating the same, then try to relaunch it.

CheckCompleteIncomplete
Node added?

Node Running?

Login into the Jenkins server and follow the below given steps:

1. Now go to Manage Jenkins.
2. Click on Nodes and Clouds option under System Configuration.
3. From the option available on the right side, click on New Node button.

4. Enter the Node name i.e linux-node.

5. Enable Permanent Agent option and click on OK.

6. Enter /home/bob under Remote root directory.

7. Enter node01 under Labels.

8. Select Only build jobs with label expressions matching this node option for Usage.

9. Select Launch Agents via SSH under Launch method.

10. Enter node01 under Host and select the credentials you created in the previous question.

11. Under Host Key Verification Strategy, select Non verifying verification strategy.

12. Leave all other options as it is and click on Save

13. Click on the linux-node and there shouldn't be any errors.

14. Just in case the linux-node node is in error state, then try to relaunch it.


