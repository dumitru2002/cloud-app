# Getting Started

### Running the Application

```
./gradlew bootRun
```

Open [http://localhost:8080](http://localhost:8080) in your browser.

### Building the Application

```
./gradlew bootJar
```

### Running the Application as a Docker Container

```
...
java -jar ./build/libs/tech-challenge-0.0.1-SNAPSHOT.jar
```

### Requirements

1. [DONE]This project should be made to run as a Docker image.
2. [DONE]Docker image should be published to a Docker registry.
3. [DONE]Docker image should be deployed to a Kubernetes cluster.
4. [DONE]Kubernetes cluster should be running on a cloud provider.
5. [DONE]Kubernetes cluster should be accessible from the internet.
6. Kubernetes cluster should be able to scale the application.
7. Kubernetes cluster should be able to update the application without downtime.
8. Kubernetes cluster should be able to rollback the application to a previous version.
9. Kubernetes cluster should be able to monitor the application.
10. Kubernetes cluster should be able to autoscale the application based on the load.
11. Application logs should be stored in a centralised logging system (Loki, Kibana, etc.)
12. Application should be able to send metrics to a monitoring system.
13. Database should be running on a separate container.
14. Storage should be mounted to the database container.

## Cloud Infrastructure

- **Provider:** AWS
- **Region:** eu-central-1 (Frankfurt)
- **Compute:** 1× EC2 t3.medium (2 vCPU, 4 GB RAM)
- **OS:** Ubuntu 22.04 LTS
- **Networking:** Default VPC, security group `cloud-app-sg`
- **Storage:** 20 GB EBS gp3 root volume
- **Public access:** Ports 80, 443, 30000-32767 open to internet; port 22 restricted to operator IP
- **Ingress controller:** Traefik (bundled with k3s, exposed on host ports 80/443 via Klipper)
- **Public URL:** http://18.192.246.204
