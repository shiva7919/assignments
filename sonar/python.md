# 🛠️ Example Voting App + SonarQube Setup Guide

### This guide walks you through setting up a Python-based voting app, running SonarQube for code quality analysis, and using SonarScanner to scan your project.

---

## 🔧 System Setup

```bash
sudo apt update
```
### Updates the package index on your system.

```bash
sudo apt install python3 python3-pip
```
### Installs Python 3 and the pip package manager.

```bash
sudo apt install python3-venv
```
### Installs the module to create Python virtual environments.

```bash
sudo apt install unzip
```
### Installs the unzip utility to extract .zip archives.

```bash
sudo apt install openjdk-11-jre-headless
sudo apt install openjdk-8-jdk
```
### Installs Java 11 and Java 8. Java 8 is needed for SonarQube 6.7.7.

## 🧬 Clone and Setup the Voting App
```bash
git clone https://github.com/Ai-TechNov/example-voting-app.git
cd example-voting-app/vote/
```
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

# 🚀 SonarQube Setup
1. Download and Extract
```bash
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-6.7.7.zip
unzip sonarqube-6.7.7.zip
```
### 2. Set Java 8
```bash
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
```

## You can check all Java paths:

```bash
update-alternatives --list java
```
### 3. Start SonarQube
```bash
cd sonarqube-6.7.7/bin/linux-x86-64/
./sonar.sh start
```
### To check status:

```bash
./sonar.sh status
```
## 🧪 SonarScanner Setup

### 1. Download and Install

```bash
curl -O https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.8.0.2856-linux.zip
unzip sonar-scanner-cli-4.8.0.2856-linux.zip
sudo mv sonar-scanner-4.8.0.2856-linux /opt/sonar-scanner
```
### 2. Add to PATH
```bash
echo 'export PATH=$PATH:/opt/sonar-scanner/bin' >> ~/.bashrc
source ~/.bashrc
```
## 📊 Run Code Analysis
### Make sure SonarQube is running, then run:
```bash
sonar-scanner \
  -Dsonar.projectKey=python \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://<YOUR_SONARQUBE_IP>:9000 \
  -Dsonar.login=<YOUR_SONARQUBE_TOKEN>
```
### Replace:

<YOUR_SONARQUBE_IP> with your actual server IP (e.g., http://44.220.150.99:9000)

<YOUR_SONARQUBE_TOKEN> with your token generated in SonarQube UI.

## 📝 Useful Commands Summary

### Command	Description
java -version	Check the active Java version.
cd <path>	Navigate directories.
ls	List directory contents.
./sonar.sh start	Start SonarQube.
./sonar.sh status	Check SonarQube status.
tail -n 100 web.log	View the last 100 lines of SonarQube log.
### ✅ Done!
You now have a working local environment with:

Python Voting App

SonarQube Server

SonarScanner for code analysis

![Image](https://github.com/user-attachments/assets/d6672613-3202-4691-b5a0-1ed3b00466f1)
![Image](https://github.com/user-attachments/assets/de185ca6-1277-4999-b910-c5740de2ada0)
![Image](https://github.com/user-attachments/assets/52d506c0-9130-40d9-bef9-1bc52da5acad)
