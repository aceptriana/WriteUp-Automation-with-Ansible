# Write Up

Buat Sebuah folder

```
mkdir quiz-1
cd quiz-1
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
buat file quiz-1_playbook.yml
```
# quiz-1_playbook.yml
---
- name: Quiz Playbook
  hosts: pod-aceptriana-managed2
  become: yes
  tasks:
    - name: Install latest versions of apache2, mariadb-server, php, and php-mysql packages
      apt:
        name:
          - apache2
          - mariadb-server
          - php
          - php-mysql
        state: latest
        update_cache: yes

    - name: Ensure apache2 service is enabled and running
      service:
        name: apache2
        state: started
        enabled: yes

    - name: Ensure mariadb service is enabled and running
      service:
        name: mariadb
        state: started
        enabled: yes

    - name: Generate web content for testing
      copy:
        content: "Adinusa quiz Playbook - aceptriana"
        dest: /var/www/html/index.php

- name: Test web server from control node
  hosts: localhost
  tasks:
    - name: Test the web service
      uri:
        url: http://pod-aceptriana-managed2/index.php
        return_content: yes
      register: webpage

    - name: Check if the web service is running and returns status 200
      assert:
        that:
          - "webpage.status == 200"
          - "'Adinusa quiz Playbook - aceptriana' in webpage.content"
```

jalankan playbook buat verifikasi
```
ansible-playbook quiz-1_playbook.yml
```
