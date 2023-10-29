# First, install the Matrix Authorization Strategy plugin and using the Project-based Matrix Authorization Strategy assign some permissions that would allow tony to build the mytest job.
Once this is done, build this job through user tony.


Note: You should use tony's credentials from the previous question.
Username: tony
Password: T0ny123

Project-based Matrix Authorization Strategy enabled?
Job built by tony?

Plugin installation steps:


1: Go to Manage Jenkins, then click on Plugins tab.

2: Click on Available section and search for Matrix Authorization Strategy plugin.

3: Then mark the box check and click on Install without restart button.

4: After that click on Restart Jenkins when installation is complete and no jobs are running.


Steps to enable Project-based Matrix Authorization Strategy:


1: Go to Manage Jenkins, then click on Security tab.

2: Select Project-based Matrix Authorization Strategy under Authorization section.

3: Click on Add User and enter user name tony. After that it will appear in the matrix.

4: Enable Read under Overall column, Build and Read under Job column for user tony.

5: Now click on Save button on your bottom of the page.

6: Login as tony user into the Jenkins server and build the job named mytest.
