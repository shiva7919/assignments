## **MY REPO: git clone https://github.com/shiva7919/jpetstore-6.git 

## ** Brief Documentation for Building & Deploying a Java Maven Web App on Ubuntu **

### **📌 System & Environment Setup **

1. Update the system
   
```bash 

Copy 

sudo apt update
```
 
2. Set hostname for the build environment 

```bash 

Copy 

sudo hostnamectl set-hostname pet-clinic_java-build 
sudo init 6
```

## **Reboot to apply hostname change **
 

 

## **📁 Clone the Project Repository **

3. Clone the JPetStore Project 

```bash 

Copy 

git clone https://github.com/shiva7919/jpetstore-6.git 
cd jpetstore-6/
```

 
4. View project structure 

```bash 

Copy 

ls 
sudo apt install tree 
tree
```
 
## **⚙️ Install Java and Maven ** 

5. Install Java JDK 11 

```bash 

Copy 

sudo apt install openjdk-11-jdk 
java -version
```
 

6. Install Maven 

```bash 

Copy 

sudo apt install maven 
mvn -v
```
 


## **🏗️ Build the Application ** 

7. Validate and Package the Application 

```bash 

Copy 

mvn validate 
mvn package
```
 

This generates a .war (Web Application Archive) file inside the target/ directory. 

 
## ** 🌐 Install and Configure Apache Tomcat **

8. Download and Extract Tomcat 

```bash 

Copy 

wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.102/bin/apache-tomcat-9.0.102.tar.gz 
tar -xvf apache-tomcat-9.0.102.tar.gz 
cd apache-tomcat-9.0.102/ 
 ```

9. Start Tomcat 

```bash 

Copy 

cd bin 
./startup.sh
```
 

10. Check Tomcat is Running 

```bash 

Copy 

curl http://54.196.150.129:8080/manager
```
 

 ## ** 🔐 Configure Tomcat Authentication **

11. Modify the context.xml files to allow remote access to the Tomcat Manager 

Files edited: 

./webapps/host-manager/META-INF/context.xml 

./webapps/manager/META-INF/context.xml 


12. Add User Roles in tomcat-users.xml 

```bash 

Copy 

cd conf/ 
sudo vi tomcat-users.xml 
 

Add the following inside <tomcat-users>: 

Xml 
```
Copy 

<role rolename="manager-gui"/> 
<role rolename="admin-gui"/> 
<user username="admin" password="admin123" roles="manager-gui,admin-gui"/> 
 

## ** 📦 Deploy the WAR File **

13. Copy WAR file to Tomcat’s webapps/ directory 

```bash 

Copy 

cp -r ~/jpetstore-6/target/*.war ~/jpetstore-6/target/apache-tomcat-9.0.102/webapps/ 
 ```

14. Verify Deployment 

```bash 

Copy 

ls ~/jpetstore-6/target/apache-tomcat-9.0.102/webapps/
```
 

## ** ✅ Test the Application ** 

Access the deployed application in a browser: 

Copy 

http://54.196.150.129:8080/jpetstore 

  
🛠️ Troubleshooting & Logs 

15. Check if Tomcat is Running 

```bash 

Copy 

ps -ef | grep tomcat
```

 16. Tomcat Logs 

```bash 

Copy 

cd ~/jpetstore-6/target/apache-tomcat-9.0.102/logs/ 
cat catalina.out
```

## ** Final OutPut: ** 

![Image](https://github.com/user-attachments/assets/c1708ca1-977b-4eeb-babe-8f72dfa407f9)
 

## ** Conclusion ** 

This process successfully builds and deploys the Pet-Clinic application using Java, Maven, and Apache Tomcat on an Ubuntu system. Following these steps ensures that you have all the required tools installed and that the application is running smoothly on the server. 
