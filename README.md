WordPress
==========

This playbook helps install WordPress on two linux servers with Http security

Requirements
-------------

You need open source projects to work properly:

- Server: ubuntu-20.04.4-live-server-amd64 ([Ubuntu])
- Ansible [core 2.12.9] ([Ansible])
- python version = 3.8.10 
- jinja version = 2.10.1

Launch Playbook
----------------

Make sure that you have connection to your servers from ansible master server with command:

```sh
ansible all -m ping
```
When all setting is right answer will be:

```
Server1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
Server2 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
```

Open Playbook:

```
sudo nano roles/wp-install/tasks/main.yml
```

Write your IP adresses in the following strings:

_For Server 1 (change 192.168.31.251 to your IP adress):_
```
80     shell: echo 192.168.31.251 www.one.wordpress.ru one.wordpress.ru >> /etc/hosts
93   when: ansible_all_ipv4_addresses == ['192.168.31.251']
157   when: ansible_all_ipv4_addresses == ['192.168.31.251']
```
_For Server 2 (change 192.168.31.121 to your IP adress):_
```
98     shell: echo 192.168.31.121 www.two.wordpress.ru two.wordpress.ru >> /etc/hosts
111   when: ansible_all_ipv4_addresses == ['192.168.31.121']
183   when: ansible_all_ipv4_addresses == ['192.168.31.121']
```

Run playbook:

```
ansible-playbook AK-ansible-task.yml -kK
```

> Note: Change IP adresses at hosts file in your computer
> "ip_address_server1" one.wordpress.ru
> "ip_adress_server2" two.wordpress.ru


To check please open following links:

www.one.wordpress.ru
www.two.wordpress.ru

License
--------

BSD

[Ansible]: <https://docs.ansible.com>
[Ubuntu]: <https://ubuntu.com>
[site1]: <https://one.wordpress.ru>
[site2]: <https://two.wordpress.ru>

Author Information
-------------------

Boris Chernov <chernov001@gmail.com>
