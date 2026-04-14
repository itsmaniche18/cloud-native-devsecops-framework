# Cloud-Native DevSecOps Framework

## 🚀 Overview

This repository contains a **formally designed, open-source DevSecOps framework** for securing cloud-native CI/CD pipelines. The framework integrates multiple security tools across different stages of the pipeline to ensure comprehensive vulnerability detection and centralized management.

It is designed focusing on **design, implementation, and evaluation** of secure CI/CD practices.

---

## 🧩 Key Features

* 🔍 **SAST (Static Application Security Testing)** using Opengrep
* 🔐 **Secrets Detection** using Gitleaks
* 📦 **SCA (Software Composition Analysis)** using Trivy (filesystem)
* 🐳 **Container Security Scanning** using Trivy (image scan)
* 🌐 **DAST (Dynamic Application Security Testing)** using OWASP ZAP
* 📊 **Centralized Vulnerability Management** via DefectDojo
* 📁 **SARIF-based reporting** for standardized output
* ⚡ Fully automated via GitHub Actions

---

## 🏗️ Architecture

The pipeline follows a multi-stage security model:

1. **Source Code Security (Shift Left)**

   * Opengrep (SAST)
   * Gitleaks (Secrets)

2. **Dependency Security**

   * Trivy Filesystem Scan (SCA)

3. **Build & Container Security**

   * Docker Build
   * Trivy Image Scan

4. **Runtime Security**

   * OWASP ZAP (DAST)

5. **Centralized Reporting**

   * DefectDojo aggregation

---

## 🔄 Pipeline Workflow

```text
Code Push → SAST + Secrets Scan → SCA → Container Build & Scan → DAST → DefectDojo
```

All tools generate reports in **SARIF/XML format**, which are uploaded and aggregated for further analysis.

---

## 🛠️ Technologies Used

* GitHub Actions
* Docker
* AWS (ECR, Secrets Manager)
* Opengrep
* Gitleaks
* Trivy
* OWASP ZAP
* DefectDojo

---

## 📦 Repository Structure

```text
.github/workflows/   # CI/CD pipeline definition
reports/             # Generated scan reports (artifacts)
docker/              # Docker build configurations
.env                 # Runtime environment variables (generated)
```

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/cloud-native-devsecops-framework.git
cd cloud-native-devsecops-framework
```

### 2. Configure Secrets in GitHub

Add the following secrets in your repository settings:

* AWS_ACCESS_KEY_ID_SANDBOX
* AWS_SECRET_ACCESS_KEY_SANDBOX
* AWS_REGION_SANDBOX
* SECRET_NAME_SANDBOX
* ECR_REPOSITORY_SANDBOX
* DEFECTDOJO_URL
* DEFECTDOJO_TOKEN
* DEFECTDOJO_PRODUCT_NAME
* DEFECTDOJO_ENGAGEMENT_*_ID

### 3. Push to Trigger Pipeline

```bash
git checkout -b sec-semgrep
git push origin sec-semgrep
```

---

## 📊 Evaluation Metrics (For Research)

This framework supports evaluation based on:

* Vulnerability detection coverage
* False positive rates
* Scan execution time
* CI/CD pipeline overhead
* Tool comparison and effectiveness

---

## 🎯 Research Contribution

This project contributes:

* A **vendor-neutral DevSecOps framework**
* Integration of multiple open-source security tools
* A **formalized pipeline model** for security gates
* Centralized vulnerability management approach

---

## 🔒 Security Gates Concept

Each stage acts as a **security gate**:

* Pipeline does not fail immediately (for research purposes)
* Findings are collected and analyzed centrally
* Can be extended to enforce thresholds (e.g., block on CRITICAL issues)

---

## 🚧 Future Improvements

* Add policy-based gating (fail on severity thresholds)
* Integrate IaC scanning (e.g., Terraform security)
* Add Kubernetes runtime security (e.g., Falco)
* Improve false-positive reduction

---

## 📄 License

This project is open-source and available under the MIT License.

---

## 👨‍🎓 Author

Master's Student in Cybersecurity
Final Year Project – DevSecOps Framework

---

## ⭐ Acknowledgements

Thanks to the open-source community for providing powerful security tools that make this framework possible.
