## Ansible HA proxy

This project contains:

1. Vagrantfile
2. Ansible roles to setup haproxy and nginx.

# Building stack

VirtualBox, Vagrant and Ansible(2.3) must be installed.

```
vagrant up
```

Running vagrant up in this project will:

1. Bring up three VM's, one for frontend(HAproxy) and two for backend(nginx).
2. forward port 80 of frontend machine to port 8080 of host machine.
3. Run Ansible playbook to provision servers.

# Test

Backend servers present a test page which display Hostname and IP address to help
understand which is which when content is served.

Once `vagrant up` command has executed successfully,

1. In the browser enter ``http://127.0.0.1:8080``
2. This should display test page served by one of the backend servers.
3. Load balancer can be accessed at ``http://127.0.0.1:8080/stats``
3.a Credentials for this page are:
    Username: admin
    Password: root_user
