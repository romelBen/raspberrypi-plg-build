# Monitor Setup using Docker Swarm
This directory focuses deploying containers on Raspberry Pis, specifically Raspberry Pi 4 (arm64).
Please understand that this project primarily focuses on arm64 not arm32. If you want to change
this project to work for your environment you must change the container image.

The containers that will be installed on your Raspberry Pi stack are these:

- Traefik (testing)
- Grafana (testing)
- Prometheus (testing)
- Node Exporter (testing)
- Alert Manager (testing)
- CloudFlare DNS (testing)
- Portainer (testing)
- Watchtower (testing)
- cAdvisor (testing)
- Vault (testing)
- Promtail (unavailable)
- Loki (unavailable)

## Environment Setup
In directory [ansible-setup](https://github.com/romelBen/devop_projects/tree/master/scripting-projects/docker-compose/plg-compose/ansible-setup), you will find two ansible scripts which will setup your environment:
- `master-playbook.yml` will setup your environment with the required libraries for docker and docker-compose
- `deploy-stack.yml` will be the final step which will transfer the this folder over to your desired host and run the stack

Whenever you make a change to the `docker-compose.yml` file, `deploy-stack.yml` will be your go-to file
to send changes to your desired hosts.

## Note
I am currently looking into setting up my docker containers to be more secured since they suffer from two distinct security issues:
- When a docker container is created, the permissions are set for all to use. In other words, Docker containers are set with root privileges. This is a big no no.
- Also, the distro you use to support Docker will punch a hole right through your firewall leaving you open to attacks. It is suggested to configure `firewalld` or `iptables` for your distro environment. There are issues when it comes to using `firewalld` which is discussed in this blog: [Secure Docker with iptables firewall and Ansible](https://ryandaniels.ca/blog/secure-docker-with-iptables-firewall-and-ansible/), so I am following Ryan Daniels approach to securing `iptables` in the Docker environment.