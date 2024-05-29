## Instructions
1. Create new folder quiz-2 for working directory.

2. Create a new file ansible.cfg, define the location of inventory on that file. also, create inventory that stored the pod-username-managed2.

3. Create the playbook named quiz-2_variables.yml and define the following variables in the vars section.

List of vars:

required_Pkg:
- apache2
- python3-urllib3
web_Service: apache2
content_File: "adinusa lab quiz variables - username"
dest_File: /var/www/html/index.html

4. Create an task block that uses those vars. Create the first task that installed required packages.

5. Create the tasks to make sure that the services are started and enabled.

6. Add a task that ensures specific content exists in pod-username-managed2. Use copy module to copy the content_File to dest_File variable.

7. Define another play for the task to be performed on the localhost. This play will test access to the web server that should be running on the pod-username-managed2 host. This play does not require privilege escalation.

8. Add a task that tests the web service running on http://pod-username-managed2/index.html from the control node using the uri module. Check for a return status code of 200. After that, save and run the playbook.

## Verification
1. Make sure you have ansible.cfg, inventory, and quiz-2_variables.yml file in the quiz-2 directory.
2. Make sure apache2, and python3-urllib3 packages are installed.
3. Make sure the apache2 service is running.
4. Make sure the /var/www/html/index.html file is exist in the managed pod-username-managed2.
5. Test webserver on pod-username-managed2. make sure the 'adinusa lab quiz variables - username' text its appears.
6. This lab is sensitive to the use of characters in the variables, pay attention to the capitalization of the characters.
