## Instructions
1. Create a new folder named quiz-1 for working directory.

2. Create a new file ansible.cfg, define the location of inventory on that file. also, create inventory that stored the pod-username-managed2.

3. Create a new playbook named quiz-1_playbook.yml. Add the necessary entries to start a first play named Quiz Playbook. define pod-username-managed2 as target host and student as the remote user ,also add require privilege escalation.

4. Add the tasks that installs the latest versions of apache2, mariadb-server, php, and php-mysql packages.

5. Add the tasks to ensure the apache2 and mariadb services are enabled and running.

6. Add the necessary entries to define the final task for generating web content for testing. Use the copy module to copy the text Adinusa quiz Playbook - username on the content parameter to /var/www/html/index.php on pod-username-managed2.

7. Define another play for the task to be performed on the control node. This play will test access to the apache2 web server that should be running on the pod-username-managed2 host. This play does not require privilege escalation, and will run on the localhost.

8. Add a task that tests the web service running on http://pod-username-managed2/index.php from the control node using the uri module. Check for a return status code of 200. After that, save and run the playbook.

## Verification
1. make sure you have ansible.cfg, inventory, and quiz-1-1_playbook.yml file in the quiz-001-1 directory.
2. Make sure apache2, mariadb-server, php, and php-mysql packages are installed.
3. Make sure the apache2 and mariadb service is running.
4. Make sure the /var/www/html/index.php file is exist in the managed pod-username-managed2.
5. Test webserver on pod-username-managed2, make sure the 'Adinusa quiz Playbook - username' text its appears.
