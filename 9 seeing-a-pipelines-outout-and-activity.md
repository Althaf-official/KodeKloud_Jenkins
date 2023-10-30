# What is BlueOcean ?

BlueOcean is a new UI experience for CI/CD in Jenkins.

# Does BlueOcean provide native integration for branch and pull requests with GitHub and Bitbucket?
yes

# What is the default URL of BlueOcean UI in Jenkins?
<jenkins url>/blue

# Install the Blue Ocean Jenkins plugin.
After the installation, verify the same by accessing the BlueOcean UI.


Note: Just in case Jenkins page gets stuck after restart please try to refresh it manually.

CheckCompleteIncomplete
Blue Ocean plugin installed?

Blue Ocean UI working?

Login into the Jenkins server and follow the below given steps:

1. Go to Manage Jenkins.
2. Click on Plugins.
3. Click on Available and search for Blue Ocean plugin.
4. Select the same and install.

5. Once installed click on Restart Jenkins when installation is complete and no jobs are running.


You can access the BlueOcean UI either by directly opening the <jenkins-url>/blue URL or by clicking on the Open Blue Ocean option, on the left side of Jenkins dashboard.


# Create a pipeline in BlueOcean as per details mentioned below:


1. Although source code is hosted on GitHub, but select Git under Where do you store your code to avoid token requirements.

2. Repository URL is https://github.com/kodekloudhub/go-webapp-sample.git.

3. Leave the Username and Password blank.

CheckCompleteIncomplete
Test the pipeline.


Login into the Jenkins server and follow the below given steps:


1. Click on Open Blue Ocean.

2 If you get a Welcome to Jenkins pop-up then click on Create a new Pipeline option, otherwise click on New Pipeline option under Pipelines.

3. Under Where do you store your code?, click on Git.

4. Enter the repository URL i.e https://github.com/kodekloudhub/go-webapp-sample.git.

5. Leave the Username and Password blank and click on Create Pipeline.

6. It will take few seconds and go-webapp-sample pipeline will be created automatically because this repository already contains a Jenkinsfile.
