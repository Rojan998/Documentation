# Python for DevOps: From Basics to Advanced

## 1. Introduction to Python for DevOps

Python is a versatile programming language widely used in DevOps for automation, configuration management, and orchestration. Its simplicity and extensive libraries make it ideal for DevOps tasks.

---

## 2. Setting Up Python

### Installing Python

- Download and install Python from [python.org](https://www.python.org/).
- Verify installation:
  ```bash
  python --version
  ```

### Setting Up a Virtual Environment

- Create a virtual environment:
  ```bash
  python -m venv env
  ```
- Activate the environment:
  - Linux/macOS: `source env/bin/activate`
  - Windows: `env\Scripts\activate`

---

## 3. Python Basics

### Variables and Data Types

```python
name = "DevOps"
age = 25
is_active = True
print(f"Name: {name}, Age: {age}, Active: {is_active}")
```

### Control Structures

```python
for i in range(5):
    print(f"Iteration {i}")

if age > 18:
    print("Adult")
else:
    print("Minor")
```

### Functions

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("DevOps Engineer"))
```

---

## 4. Working with Files

### Reading and Writing Files

```python
# Writing to a file
with open("example.txt", "w") as file:
    file.write("Hello, DevOps!")

# Reading from a file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

### Real-Time Example: Log Rotation

```python
import os
import shutil

def rotate_logs(log_dir, backup_dir):
    if not os.path.exists(backup_dir):
        os.makedirs(backup_dir)
    for log_file in os.listdir(log_dir):
        shutil.move(os.path.join(log_dir, log_file), backup_dir)

rotate_logs("/var/logs", "/var/logs_backup")
```

---

## 5. Networking with Python

### Using `socket` for Networking

```python
import socket

hostname = socket.gethostname()
ip_address = socket.gethostbyname(hostname)
print(f"Hostname: {hostname}, IP Address: {ip_address}")
```

### Real-Time Example: Port Scanner

```python
import socket

def scan_ports(host, ports):
    for port in ports:
        with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
            result = s.connect_ex((host, port))
            if result == 0:
                print(f"Port {port} is open")
            else:
                print(f"Port {port} is closed")

scan_ports("127.0.0.1", [22, 80, 443])
```

---

## 6. Automating Tasks

### Automating with `subprocess`

```python
import subprocess

def run_command(command):
    result = subprocess.run(command, shell=True, capture_output=True, text=True)
    print(result.stdout)

run_command("ls -l")
```

### Real-Time Example: Automating Backups

```python
import os
import shutil

def backup_files(source_dir, backup_dir):
    if not os.path.exists(backup_dir):
        os.makedirs(backup_dir)
    shutil.copytree(source_dir, backup_dir, dirs_exist_ok=True)

backup_files("/data", "/backup/data")
```

---

## 7. Working with APIs

### Using `requests` Library

```python
import requests

response = requests.get("https://api.github.com")
print(response.json())
```

### Real-Time Example: Fetching Weather Data

```python
import requests

def get_weather(city):
    api_key = "your_api_key"
    url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}"
    response = requests.get(url)
    data = response.json()
    print(f"Weather in {city}: {data['weather'][0]['description']}")

get_weather("London")
```

---

## 8. Infrastructure as Code (IaC)

### Using Python with Terraform

```python
import os

def apply_terraform():
    os.system("terraform init && terraform apply -auto-approve")

apply_terraform()
```

### Real-Time Example: Managing AWS Resources

```python
import boto3

ec2 = boto3.client("ec2")
instances = ec2.describe_instances()
for reservation in instances["Reservations"]:
    for instance in reservation["Instances"]:
        print(f"Instance ID: {instance['InstanceId']}, State: {instance['State']['Name']}")
```

---

## 9. Monitoring and Logging

### Monitoring System Metrics

```python
import psutil

cpu = psutil.cpu_percent(interval=1)
memory = psutil.virtual_memory()
print(f"CPU Usage: {cpu}%, Memory Usage: {memory.percent}%")
```

### Real-Time Example: Log Monitoring

```python
import time

def monitor_logs(log_file):
    with open(log_file, "r") as file:
        file.seek(0, 2)  # Move to the end of the file
        while True:
            line = file.readline()
            if line:
                print(line.strip())
            time.sleep(1)

monitor_logs("/var/log/syslog")
```

---

## 10. Advanced Topics

### Multithreading

```python
import threading

def print_numbers():
    for i in range(5):
        print(i)

thread = threading.Thread(target=print_numbers)
thread.start()
thread.join()
```

### Real-Time Example: Parallel File Processing

```python
import threading

def process_file(file):
    print(f"Processing {file}")

files = ["file1.txt", "file2.txt", "file3.txt"]
threads = [threading.Thread(target=process_file, args=(file,)) for file in files]

for thread in threads:
    thread.start()

for thread in threads:
    thread.join()
```

---

## 11. Best Practices

- **Use Virtual Environments**: Isolate dependencies for each project.
- **Write Modular Code**: Break scripts into reusable functions.
- **Handle Exceptions**: Use `try-except` blocks to handle errors.
- **Use Logging**: Replace `print` statements with the `logging` module.
- **Follow PEP 8**: Adhere to Python's style guide.

---

## 12. Resources and Further Reading

- [Python Official Documentation](https://docs.python.org/)
- [Real Python](https://realpython.com/)
- [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/)
- [Python for DevOps Book](https://www.pythonfordevops.com/)

---
