# Monitor Setup using Docker Swarm
This directory focuses deploying containers on Raspberry Pis, specifically Raspberry Pi 4 (arm64).
Please understand that this project primarily focuses on arm64 not arm32. If you want to change
this project to work for your environment you must change the container image.

The containers that will be installed on your Raspberry Pi are these:

- Grafana
- Prometheus
- cAdvisor
- Node Exporter
- Promtail (in the works)
- Loki (in the works)

## Environment Setup
In directory [ansible-setup] (https://github.com/romelBen/devop_projects/tree/master/scripting-projects/docker-compose/plg-compose/ansible-setup), you will find two scripts that will setup your environment:
`master-playbook.yml` which setups your environment with the required libraries for docker and docker-compose, and `deploy-stack.yml` which transfers this folder and runs the stack over on your desired hosts.

Whenever you make a change to the `docker-compose.yml` file, `deploy-stack.yml` will be your go-to file
to send changes to your desired hosts.