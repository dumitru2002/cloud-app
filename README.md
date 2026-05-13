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

- [x] 1. This project should be made to run as a Docker image.
- [x] 2. Docker image should be published to a Docker registry.
- [x] 3. Docker image should be deployed to a Kubernetes cluster.
- [x] 4. Kubernetes cluster should be running on a cloud provider.
- [x] 5. Kubernetes cluster should be accessible from the internet.
- [x] 6. Kubernetes cluster should be able to scale the application.
- [x] 7. Kubernetes cluster should be able to update the application without downtime.
- [x] 8. Kubernetes cluster should be able to rollback the application to a previous version.
- [x] 9. Kubernetes cluster should be able to monitor the application.
- [x] 10. Kubernetes cluster should be able to autoscale the application based on the load.
- [x] 11. Application logs should be stored in a centralised logging system (Loki, Kibana, etc.)
- [x] 12. Application should be able to send metrics to a monitoring system.
- [x] 13. Database should be running on a separate container.
- [x] 14. Storage should be mounted to the database container.

## Cloud Infrastructure

- **Provider:** AWS
- **Region:** eu-central-1 (Frankfurt)
- **Compute:** 1× EC2 t3.medium (2 vCPU, 4 GB RAM)
- **OS:** Ubuntu 22.04 LTS
- **Networking:** Default VPC, security group `cloud-app-sg`
- **Storage:** 20 GB EBS gp3 root volume
- **Public access:** Ports 80, 443, 30000-32767 open to internet; port 22 restricted to operator IP
- **Ingress controller:** Traefik (bundled with k3s, exposed on host ports 80/443 via Klipper)
- **Monitoring:** kube-prometheus-stack (Prometheus, Grafana, kube-state-metrics, node-exporter)
- **Logging:** Loki + Promtail
- **Metrics endpoint:** /actuator/prometheus on cloud-app
- **Database:** PostgreSQL 16 (separate container)
- **DB credentials:** Kubernetes Secret `postgres-credentials`
- **DB storage:** 5Gi PersistentVolumeClaim (local-path StorageClass)
- **App ↔ DB connection:** in-cluster service DNS (`postgres:5432`), JPA + HikariCP

## Public URLs

- App: https://app.yourdomain.com
- Grafana: https://grafana.yourdomain.com (admin / demoAdmin123)

## TLS

- Provider: Let's Encrypt
- Automation: cert-manager
- Issuer: ClusterIssuer `letsencrypt-prod`
- Renewal: automatic, 30 days before expiry
