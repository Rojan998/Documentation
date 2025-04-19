# YAML for DevOps: From Basics to Advanced

## 1. Introduction to YAML

YAML (YAML Ain't Markup Language) is a human-readable data serialization format commonly used in DevOps for configuration files, CI/CD pipelines, and infrastructure as code (IaC). Its simplicity and readability make it ideal for managing complex configurations.

---

## 2. YAML Basics

### Key-Value Pairs

```yaml
name: DevOps
age: 25
is_active: true
```

### Lists

```yaml
tools:
  - Docker
  - Kubernetes
  - Terraform
```

### Nested Structures

```yaml
person:
  name: John
  details:
    age: 30
    role: DevOps Engineer
```

---

## 3. YAML Syntax and Rules

### Indentation

- Use spaces, not tabs.
- Indentation defines structure.

### Comments

```yaml
# This is a comment
name: DevOps
```

### Scalars

- Strings, numbers, booleans, and null values.

```yaml
string: 'Hello'
number: 42
boolean: true
null_value: null
```

### Multi-Line Strings

```yaml
description: |
  This is a multi-line
  string in YAML.
```

### Anchors and Aliases

```yaml
default: &default_settings
  retries: 3
  timeout: 30

custom:
  <<: *default_settings
  timeout: 60
```

---

## 4. Working with YAML in DevOps

### YAML for Docker Compose

```yaml
version: '3.8'
services:
  web:
    image: nginx
    ports:
      - '80:80'
  db:
    image: postgres
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: password
```

### YAML for Ansible Playbooks

```yaml
- name: Install and start Apache
  hosts: webservers
  tasks:
    - name: Install Apache
      apt:
        name: apache2
        state: present
    - name: Start Apache
      service:
        name: apache2
        state: started
```

---

## 5. YAML in CI/CD Pipelines

### GitHub Actions Workflow

```yaml
name: CI Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: 3.9
      - name: Install dependencies
        run: pip install -r requirements.txt
      - name: Run tests
        run: pytest
```

### GitLab CI/CD

```yaml
stages:
  - build
  - test

build-job:
  stage: build
  script:
    - echo "Building the application"

test-job:
  stage: test
  script:
    - echo "Running tests"
```

---

## 6. YAML for Kubernetes

### Kubernetes Pod Definition

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    app: my-app
spec:
  containers:
    - name: nginx-container
      image: nginx
      ports:
        - containerPort: 80
```

### Kubernetes Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: nginx
          image: nginx:1.21
          ports:
            - containerPort: 80
```

---

## 7. YAML for Configuration Management

### Terraform YAML Configuration

```yaml
provider:
  name: aws
  region: us-east-1

resource:
  aws_instance:
    my_instance:
      ami: ami-12345678
      instance_type: t2.micro
```

### Helm Chart Values

```yaml
replicaCount: 3
image:
  repository: nginx
  tag: '1.21'
  pullPolicy: IfNotPresent
service:
  type: ClusterIP
  port: 80
```

---

## 8. Advanced YAML Features

### Using Environment Variables

```yaml
environment:
  - name: DATABASE_URL
    value: ${DATABASE_URL}
```

### Conditional Logic (e.g., in CI/CD)

```yaml
jobs:
  deploy:
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to production
        run: ./deploy.sh
```

### YAML Validation

- Use tools like `yamllint` or `pyyaml` to validate YAML files.

---

## 9. Best Practices

- **Use Consistent Indentation**: Stick to 2 or 4 spaces.
- **Add Comments**: Explain complex configurations.
- **Validate YAML**: Use linters to catch syntax errors.
- **Avoid Hardcoding**: Use environment variables where possible.
- **Keep It Simple**: Avoid deeply nested structures.

---

## 10. Resources and Further Reading

- [YAML Official Documentation](https://yaml.org/)
- [Learn YAML in 5 Minutes](https://learnxinyminutes.com/docs/yaml/)
- [YAML Linter](https://yamllint.readthedocs.io/)
- [Kubernetes YAML Basics](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/)

---
