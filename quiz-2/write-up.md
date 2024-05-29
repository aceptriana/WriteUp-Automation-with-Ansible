# Write Up

Buat Sebuah folder

```
mkdir quiz-2
cd quiz-2

```
buat file ansible.cfg
```
# ansible.cfg
[defaults]
inventory = ./inventory

```
buat file inventory
```
# inventory
[pod-aceptriana-managed2]
pod-aceptriana-managed2 ansible_user=student ansible_become=yes
```
buat file quiz-2_variables.yml
```
# quiz-2_variables.yml
---
- name: Setup Web Server
  hosts: pod-aceptriana-managed2
  become: yes
  vars:
    required_Pkg:
      - apache2
      - python3-urllib3
    web_Service: apache2
    content_File: "adinusa lab quiz variables - aceptriana"
    dest_File: /var/www/html/index.html
  tasks:
    - name: Install required packages
      apt:
        name: "{{ required_Pkg }}"
        state: present
        update_cache: yes

    - name: Ensure apache2 service is started and enabled
      service:
        name: "{{ web_Service }}"
        state: started
        enabled: yes

    - name: Ensure specific content exists in pod-aceptriana-managed2
      copy:
        content: "{{ content_File }}"
        dest: "{{ dest_File }}"

- name: Test web server from control node
  hosts: localhost
  tasks:
    - name: Test the web service
      uri:
        url: http://pod-aceptriana-managed2/index.html
        return_content: yes
      register: webpage

    - name: Check if the web service is running and returns status 200
      assert:
        that:
          - webpage.status == 200
          - "'adinusa lab quiz variables - aceptriana' in webpage.content"

```

jalankan playbook buat verifikasi
```
ansible-playbook quiz-2_variables.yml
```
