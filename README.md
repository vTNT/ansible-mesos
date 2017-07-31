Mesos Role
=========

Configure and run Mesos components (master or slaves)

This role has been specifically developed to be used for the deployment of Mesos in the framework of INDIGO-DataCloud project.

Role Variables
--------------

Common vars:

- `mesos_install_mode`: "master" or "slave"
- `zookeeper_peers`
- `zookeeper_client_port` (default: 2181)


Example Playbook
----------------

This is an example of how to use `mesos` role:

For "master" nodes:

    ---
    - name: Test the plabybook API.
      hosts: all
      remote_user: root
      gather_facts: yes
      roles:
        - role: ansible-mesos
          mesos_install_mode: "master"
          mesos_ip : "{{ ansible_eth0.ipv4.address }}"
          zookeeper_peers: ["10.1.1.1"]
          mesos_containerizers: "mesos"

For "slave" nodes:

    ---
    - name: Test the plabybook API.
      hosts: all
      remote_user: root
      gather_facts: yes
      roles:
        - role: ansible-mesos
          mesos_install_mode: "slave"
          mesos_ip : "{{ ansible_eth0.ipv4.address }}"
          zookeeper_peers: ["10.1.1.1"]
          mesos_containerizers: "mesos"

License
-------

Apache Licence v2 [1]

[1] http://www.apache.org/licenses/LICENSE-2.0
