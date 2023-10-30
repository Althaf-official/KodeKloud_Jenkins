# What is a Jenkinsfile?
A Jenkinsfile is a text file that contains the definition of a Jenkins Pipeline.

# Install Pipeline Jenkins plugin?


Note: Just in case Jenkins page gets stuck after restart please try to refresh it.

CheckCompleteIncomplete
Pipeline plugin is installed?

Login into the Jenkins server and follow the below given steps:


1. Go to Manage Jenkins.

2. Click on Plugins.

3. Under Available, search for Pipeline plugin.

4. Select it and install.

5. Once installed click on Restart Jenkins when installation is complete and no jobs are running.

# Create a pipeline job named hello-world, it should just echo the Hello World string.



# We have a pipeline job named go-test but its incomplete.

Complete the same by adding the required stages/steps as per details mentioned below:


1. Clone a git repository.

git 'https://github.com/kodekloudhub/go-webapp-sample.git'


2. Run a shell command go test ./...

sh 'go test ./...'




Note: You can name the stages as per your choice.

CheckCompleteIncomplete
Test the go-test job.




Login into the Jenkins server and follow the below given steps:


1. Click on go-test job.

2 Open the job configuration by clicking on Configure button.

3. Under the pipeline section, complete the Script and the final code should look like as below


pipeline {
    agent {
        label {
            label 'master'
            customWorkspace "${JENKINS_HOME}/${BUILD_NUMBER}/"
        }
    }
    environment {
        Go111MODULE='on'
    }
    stages {
        stage('Test') {
            steps {
                git 'https://github.com/kodekloudhub/go-webapp-sample.git'
                sh 'go test ./...'
            }
        }
    }
}


4. Finally save the job.


# Now modify the go-test pipeline job as per details mentioned below:


1. Remove the sh 'go test ./...' step.

2. Add an another stage (name it as per your choice) to build a docker image from the cloned code. The required Jenkins plugins have already been installed i.e Docker and Docker pipeline. The image should be tagged as adminturneddevops/go-webapp-sample

CheckCompleteIncomplete
Build the job.

Verify the job.

Verify the docker image.

ogin into the Jenkins server and follow the below given steps:


1. Click on go-test job.

2 Open the job configuration by clicking on Configure button.

3. Under the pipeline section, modify the Script and the final code should look like as below


pipeline {
    agent {
        label {
            label 'master'
            customWorkspace "${JENKINS_HOME}/${BUILD_NUMBER}/"
        }
    }
    environment {
        Go111MODULE='on'
    }
    stages {
        stage('Test') {
            steps {
                git 'https://github.com/kodekloudhub/go-webapp-sample.git'
            }
        }
        stage('build') {
            steps {
                script{
                    image = docker.build("adminturneddevops/go-webapp-sample")
                }
            }
        }
    }
}


4. Finally save the job.


# Now that you have built the docker image so let's modify the go-test pipeline job to deploy an app using this docker image. Find below more details:


1. Add an another step to run a docker container using the docker image you are building in this pipeline itself. Make sure to map container port 8000 with docker host port 8090. This is the step you can add:


sh "docker run -p 8090:8000 -d adminturneddevops/go-webapp-sample"
CheckCompleteIncomplete
Build the job.

Verify the job.

Verify the app.


Login into the Jenkins server and follow the below given steps:


1. Click on go-test job.

2 Open the job configuration by clicking on Configure button.

3. Under the pipeline section, modify the Script and the final code should look like as below


pipeline {
    agent {
        label {
            label 'master'
            customWorkspace "${JENKINS_HOME}/${BUILD_NUMBER}/"
        }
    }
    environment {
        Go111MODULE='on'
    }
    stages {
        stage('Test') {
            steps {
                git 'https://github.com/kodekloudhub/go-webapp-sample.git'
            }
        }
        stage('build') {
            steps {
                script{
                    image = docker.build("adminturneddevops/go-webapp-sample")
                    sh "docker run -p 8090:8000 -d adminturneddevops/go-webapp-sample"
                }
            }
        }
    }
}


4. Finally save the job.


