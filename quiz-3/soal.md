## Instructions
1. Create a new folder in the user home directory. Name it quiz-3.

2. In the quiz-3 folder, create a playbook with the tasks below and execute to the pod-username-managed1 and pod-username-managed2 nodes as a group called webservers:

- Name the file of playbook with quiz-3_j2template.yml

- Add mariadb 10.9 and nginx repository to the /etc/apt/sources.list.d/ using jinja2 template.

- Name the nginx repository file with nginx.list, and name the file of jinja2 template with nginx.list.j2.

- Name the mariadb repository file with mariadb.list, and name the file of jinja2 template with mariadb.list.j2.

- Create task that update the repository.

- Create task that install nginx=1.23.1-1~jammy, mariadb-server-10.9 and mariadb-client-10.9.

- Create task that make sure to start dan enable service nginx and mariadb-server (ensure the value of state in the service section is started), and make sure to write this on below format:
```
 - name: example name of service
      service: name=<service> state=<state of service> anotherkey=<another rvalue>
```

## Verification
1. Make sure the ansible.cfg, inventory, nginx.list.j2, mariadb.list.j2, and quiz-3_j2template.yml exist in the quiz-001-3 directory.
2. Make sure the nginx=1.23.1-1~jammy, mariadb-server-10.9, and mariadb-client-10.9 packages are installed.
3. Make sure the /etc/apt/sources.list.d/nginx.list and /etc/apt/sources.list.d/mariadb.list file is exist in the managed pod-username-managed1 and pod-username-managed2.
4. Make sure the nginx and mariadb-server service are running and enabled.
