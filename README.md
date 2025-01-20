
# **EKS-K8S Project 🚀**

Welcome to our awesome project! 🎉 This project demonstrates the deployment of a WordPress application on a Kubernetes (K8S) cluster hosted on Amazon EKS (Elastic Kubernetes Service). The deployment includes key Kubernetes resources such as Deployments, Services, Ingress, Persistent Volumes, Persistent Volume Claims, Horizontal Pod Autoscalers, and integration with Let's Encrypt for SSL certificates.

## **Features 🌟**

### **1. WordPress Deployment 📝**
- WordPress is deployed using a Kubernetes Deployment object.
- Includes environment variables to connect to the MySQL database.
- Configured with a Persistent Volume for data persistence.

### **2. MySQL Deployment 🗄️**
- MySQL is deployed as a separate Deployment.
- Configured with its own Persistent Volume and Persistent Volume Claim for database storage.
- Secure environment variables are stored in a Kubernetes Secret.

### **3. Ingress Configuration 🌐**
- Ingress is used to expose the WordPress application to the internet.
- Configured with an NGINX Ingress Controller.
- Integrated with Let's Encrypt for automatic SSL certificate generation.

### **4. Persistent Volumes (PVs) and Persistent Volume Claims (PVCs) 💾**
- Persistent Volumes are used to ensure data persistence for both WordPress and MySQL.
- Claims are bound to the respective volumes for storage allocation.

### **5. Horizontal Pod Autoscaler (HPA) 📈**
- HPA is configured to scale the WordPress Deployment based on CPU utilization.
- Ensures high availability and scalability during traffic spikes.

### **6. Probes for Health Checks 🩺**
- **Liveness Probe**: Ensures the application is running and responsive.
- **Readiness Probe**: Confirms the application is ready to handle requests.
- **Startup Probe**: Ensures the container initializes properly before receiving traffic.

### **7. Cluster Issuer and SSL Integration 🔒**
- A ClusterIssuer is configured for Let's Encrypt to handle SSL certificates.
- Certificates are automatically renewed and managed.

## **Kubernetes Resources 🛠️**

### **WordPress Deployment (`wordpress-deployment.yaml`) 📋**
- Defines the WordPress application.
- Configured with Probes for monitoring.
- Attached to a Persistent Volume Claim for data persistence.

### **MySQL Deployment 🗃️**
- Separate Deployment for MySQL database.
- Includes environment variables for secure configuration.
- Uses a Persistent Volume Claim for storage.

### **Ingress Configuration (`ingress.yaml`) 🌍**
- Routes traffic to the WordPress Service.
- Uses NGINX as the ingress controller.
- Configured with annotations for SSL redirection and Let's Encrypt integration.

### **Horizontal Pod Autoscaler (`hpa.yaml`) 📊**
- Monitors CPU utilization to dynamically scale the number of WordPress pods.
- Ensures application availability during varying workloads.

### **Cluster Issuer (`cluster-issuer.yaml`) 📄**
- Configures Let's Encrypt to issue SSL certificates for the domain.

## **Requirements 🧩**

### **Infrastructure 🏗️**
- Amazon EKS cluster.
- NGINX Ingress Controller installed.
- cert-manager installed for SSL management.

### **Tools 🛠️**
- `kubectl` for managing the cluster.
- `helm` for installing the NGINX Ingress Controller and cert-manager.

## **Setup Instructions 📝**

### **Clone the Repository 🐙**
```bash
git clone https://github.com/OmerWafaey/EKS-K8S.git
cd EKS-K8S
```

### **Apply Kubernetes Resources ⚙️**
```bash
kubectl apply -f mysql-pv.yaml
kubectl apply -f mysql-pvc.yaml
kubectl apply -f mysql-secret.yaml
kubectl apply -f wordpress-deployment.yaml
kubectl apply -f ingress.yaml
kubectl apply -f cluster-issuer.yaml
kubectl apply -f hpa.yaml
```

### **Verify Resources ✅**
```bash
kubectl get pods
kubectl get svc
kubectl get ingress
kubectl get hpa
```

### **Access the Application 🌐**
- Obtain the Ingress LoadBalancer IP or DNS name:
  ```bash
  kubectl get ingress
  ```
- Open the application in your browser using the provided domain.

## **Troubleshooting 🔍**

### **Ingress Not Accessible 🚫**
- Ensure the NGINX Ingress Controller is correctly installed and the LoadBalancer service is active.

### **SSL Certificate Issues ❌**
- Verify the ClusterIssuer configuration and ensure Let's Encrypt rate limits are not exceeded.

### **Pods Not Scaling ⚖️**
- Check HPA metrics using:
  ```bash
  kubectl describe hpa wordpress-hpa
  ```

## **Future Improvements 🚀**
- Integrate monitoring tools like Prometheus and Grafana for enhanced visibility.
- Implement logging solutions such as ELK Stack.
- Add support for CI/CD pipelines.

## **License 📄**
This project is licensed under the MIT License.

## **Author ✍️**
**Omer Wafaey**

- GitHub: [OmerWafaey](https://github.com/OmerWafaey)
- Email: [omerwafaey@gmail.com](mailto:omerwafaey14@gmail.com)
