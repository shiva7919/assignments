#  Part 1: Setting Up SonarQube Server on Ubuntu (t2.medium)
##  1. Launch a t2.medium Ubuntu Instance
- Use AWS EC2 and select Ubuntu 20.04/22.04 LTS.
- Choose a t2.medium instance.
- Make sure port 9000 is open in the security group (for SonarQub
e UI access).
##  2. Update System Packages
```bash
sudo apt update
```
##  3. Install Java (Required for SonarQube)
```bash
sudo apt install openjdk-11-jre-headless -y
```
✅ Verify installation:
```bash
java -version
```
##  4. Download and Extract SonarQube
```bash
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-6.7.7.zip
sudo apt install unzip -y
unzip sonarqube-6.7.7.zip
```
## 5. Navigate to the SonarQube Start Script
```bash
cd sonarqube-6.7.7/bin/linux-x86-64/
```
## ▶️ 6. Start SonarQube Server
```bash
./sonar.sh start
```
✅ Check status:
```bash
./sonar.sh status
```
##  7. Access SonarQube Web Interface
Open your browser and go to:
```bash
http://<your-t2.medium-IP>:9000
```
Default credentials:
- Username: admin
- Password: admin
ὑ After first login, reset your password and generate a user token under: My Account > Security > Generate# Ὃ Part 2: Java Project & Sonar Analysis (on t2.micro)
##  1. Launch a t2.micro Ubuntu Instance
- Choose Ubuntu 20.04/22.04 LTS.
- Ensure it can reach the t2.medium instance over port 9000.
##  2. Update System & Install Dependencies
```bash
sudo apt update
sudo apt install openjdk-11-jre-headless -y
sudo apt install git maven -y
```
### ✅ Check versions:
```bash
java -version
git --version
mvn -v
```
## 3. Clone Java Project
```bash
git clone https://github.com/shiva7919/jpetstore-6.git
cd jpetstore-6
```
##  4. Build the Project
```bash
mvn clean package
```
##  5. Run SonarQube Analysis

```bash
mvn sonar:sonar -Dsonar.host.url=http://<your-sonarqube-server-ip>:9000 -Dsonar.login=<your-sonarq
```
Replace:
- `<your-sonarqube-server-ip>` with the IP of your t2.medium instance
- `<your-sonarqube-token>` with the token you generated in SonarQube UI
Example:

```bash
mvn sonar:sonar -Dsonar.host.url=http://100.27.209.202:9000 -Dsonar.login=41d074c77a69cc94d04a6a
```
## ✅ 6. View Results in SonarQube Dashboard
Open:
```bash
http://<your-sonarqube-server-ip>:9000
```
Navigate to Projects to see the analysis report of your Java project.
You'll find:
- Code smells
- Bugs
- Vulnerabilities
- Code coverage
- Maintainability metrics

# Notes and Tips
- SonarQube 6.7.7 is a Long-Term Support (LTS) version but a bit old; newer versions require Java 17+ and - Ensure the SonarQube server is running whenever analysis is being triggered.
- You can automate this with Jenkins or GitHub Actions later.

![Image](https://github.com/user-attachments/assets/89fe5f73-57dc-4dbb-bedd-2a0126ad7bfe)
![Image](https://github.com/user-attachments/assets/a83d1e91-9de2-4a19-b528-4d39af51e352)
![Image](https://github.com/user-attachments/assets/befd5dcb-e4fc-4545-ac0f-bce8db218240)
![Image](https://github.com/user-attachments/assets/8e58b388-54aa-4716-a717-eb7d831858a8)
![Image](https://github.com/user-attachments/assets/caa8cc75-209f-4e49-b39d-841dbb21a5e0)
![Image](https://github.com/user-attachments/assets/88e6df99-d907-4f36-a9c9-f9b2fdf43e2e)
![Image](https://github.com/user-attachments/assets/df9cdac8-f9b7-4880-8039-83aa183692d6)
![Image](https://github.com/user-attachments/assets/8b58db44-251e-4d20-8c77-8cab272d2c23)