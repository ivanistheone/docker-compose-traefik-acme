# docker-compose-traefik-acme

A sample project that uses docker-compose and traefik for HTTP ingress, including Let's Encrypt certs.


Install fabric
--------------
In order to automate the steps docker host provisioning, we'll use Fabric,
which means we need to setup a Python environment for this project.

    virtualenv -p python3 venv
    source venv/bin/activate
    pip install -r requirements.txt


Configure remote host
---------------------
Edit `fabfile.py` and edit the values of `env.hosts` and `env.user` setting them
to the info of the new hosts (IP address and admin user with sudo capabilities).


Install docker on remote host
-----------------------------

    fab install_docker



Docker compose
--------------
Following the steps in the [traefik docs](https://doc.traefik.io/traefik/https/acme/)
we copy the file `docker-compose.yml` and applied the modifications to the test
domain we want to use, then simply run:

    fab dcup


You can "tail" the logs using the command `fab dclogs:"-f"`.

Everything seems to be running fine. We've got certs, we've got routing. Yeey!