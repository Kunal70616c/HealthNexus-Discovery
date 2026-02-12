## 🛰️ HealthNexus-Discovery

**HealthNexus-Discovery** is the central service registry for the HealthNexus microservices ecosystem. Built using **Netflix Eureka Server**, it acts as the "phonebook" for the architecture, allowing various services to discover and communicate with each other dynamically without hardcoded network locations.

---

### 🚀 Overview

In this ecosystem, **HealthNexus-Discovery** is responsible for:

* **Service Registration**: Maintaining a real-time list of all active service instances (API, Gateway, etc.).
* **Health Monitoring**: Using heartbeats to ensure traffic is only routed to healthy instances.
* **De-coupled Communication**: Enabling the **HealthNexus-Gateway** to route requests based on service names rather than static IPs.

---

### 🛠️ Tech Stack

* **Framework**: Spring Boot 3.x
* **Service Discovery**: Spring Cloud Netflix Eureka Server
* **Language**: Java 17+

---

### 🏷️ Annotation Reference

The following Spring Boot and Spring Cloud annotations are used to power this discovery server:

| Annotation | Origin | Description |
| --- | --- | --- |
| `@SpringBootApplication` | Spring Boot | Marks the main class of a Spring Boot application. It triggers auto-configuration, component scanning, and allows for defining extra configurations. |
| `@EnableEurekaServer` | Spring Cloud | Specifically tells Spring Boot to act as a **Eureka Discovery Server**, initializing the registry and the dashboard. |

---

### ⚙️ Configuration Details (`application.properties`)

The server is configured to run as a **standalone registry**, meaning it does not attempt to register with itself or fetch a registry from peers.

* **Port**: `8761` (The standard default port for Eureka).
* **Self-Registration**: Disabled (`register-with-eureka=false`).
* **Fetch Registry**: Disabled (`fetch-registry=false`).
* **Heartbeat Optimization**: Optimized for development with a 2-second renewal and expiration interval to quickly detect service status changes.

---

### 📂 Project Structure

```text
sh.surge.kunal.healthnexus/
└── EurekadiscoveryserverApplication.java  # Main class with @EnableEurekaServer
resources/
└── application.properties                # Core Eureka & Server settings

```

---

### 🖥️ Getting Started

1. **Clone the repository:**
```bash
git clone https://github.com/your-username/HealthNexus-Discovery.git

```


2. **Run the application:**
```bash
mvn spring-boot:run

```


3. **Access the Dashboard:**
Open your browser and navigate to `http://localhost:8761` to view the Eureka status page and see all registered instances in real-time.

---
