## 🏗️ OCR API - Architecture Overview

The **OCR API** is a cloud-native microservice designed to perform Optical Character Recognition (OCR) on uploaded documents or images.  
It is deployed on **Kubernetes (AWS EKS)** and exposed via an **AWS Load Balancer**, with **Cloudflare** providing DNS and HTTPS termination.

### 🔹 High-Level Architecture

```
flowchart TD
    A[User / Browser / Client App] -->|HTTPS Request| B["Cloudflare CDN + SSL"]
    B -->|HTTP| C["AWS Load Balancer - ELB"]
    C --> D["Kubernetes Cluster - EKS"]
    D --> E["OCR Service Pod - Spring Boot"]
    E --> F["Tesseract OCR Engine"]
    E --> G["Redis - Cache / Storage"]
    F -->|Extracted Text| E
    E -->|JSON Response| A

    style A fill:#f6f8fa,stroke:#333,stroke-width:1px
    style B fill:#ffdd99,stroke:#333,stroke-width:1px
    style C fill:#ffd580,stroke:#333,stroke-width:1px
    style D fill:#d6e9c6,stroke:#333,stroke-width:1px
    style E fill:#b3e6ff,stroke:#333,stroke-width:1px
    style F fill:#c2f0c2,stroke:#333,stroke-width:1px
    style G fill:#f4cccc,stroke:#333,stroke-width:1px
```
```
