
### 📘 SonarQube Setup and Java Project Analysis Guide

#### 🔧 Launch SonarQube Server

1. **Update your server packages**
   ```bash
   sudo apt update -y
   ```

2. **Install Java 17 (required by SonarQube)**
   ```bash
   sudo apt install openjdk-17-jre-headless -y
   ```

3. **Install unzip utility**
   ```bash
   sudo apt install -y unzip
   ```

4. **Download and extract SonarQube**
   ```bash
   wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-25.4.0.105899.zip
   unzip sonarqube-25.4.0.105899.zip
   ```

5. **Start SonarQube**
   ```bash
   cd sonarqube-25.4.0.105899/bin/linux-x86-64
   ./sonar.sh start
   ./sonar.sh status
   ```

6. **Access SonarQube Dashboard**
   - Open a browser and navigate to:  
     `http://<your-ec2-public-ip>:9000`

![](./images/sonar%20server.png)
   - **Login Credentials:**  
     `Username: admin`  
     `Password: admin`
   - Reset the admin password upon first login.

---

#### 🚀 Configure SonarQube for Java Project

1. **Go to Projects → Create Project**

2. **Choose `Local` Project**

3. **Provide Project Details**
   - Project Key: `java`
   - Project Name: `java`

4. **Choose Configuration**
   - Select `Use global settings`
   - Then choose `Locally`

5. **Generate Authentication Token**
   - Click on `Generate`
   - Copy the generated token
   - Click `Continue`

6. **Copy the Maven command snippet shown**

---

#### 💻 Launch Java Build Server

1. **Clone your Java project**
   ```bash
   git clone https://github.com/<your-java-repo>.git
   cd Sample_Tomcat_Project
   ```

2. **Package the project using Maven**
   ```bash
   mvn package
   ```

3. **Run SonarQube analysis**
   ```bash
   mvn clean verify sonar:sonar \
     -Dsonar.projectKey=java \
     -Dsonar.projectName='java' \
     -Dsonar.host.url=http://<ec2_public_ip>:9000 \
     -Dsonar.token=sqp_<token>
   ```

---
![](./images/sonar%20analysis%20output.png)

####  Notes

- Ensure your EC2 security group allows inbound access to port `9000`.
- You can check analysis results in the SonarQube UI under your project.
- Keep your SonarQube token safe and avoid committing it to any version control system.
