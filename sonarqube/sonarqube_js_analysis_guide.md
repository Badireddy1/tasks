
### 📘 SonarQube Setup and JavaScript Project Analysis Guide

#### 🚀 Configure SonarQube for JavaScript Project

1. **Go to Projects → Create Project**

2. **Choose `Local` Project**

3. **Provide Project Details**
   - Project Key: `javascript`
   - Project Name: `javascript`

4. **Choose Configuration**
   - Select `Use global settings`
   - Then choose `Locally`

5. **Generate Authentication Token**
   - Click on `Generate`
   - Copy the generated token
   - Click `Continue`

6. **Copy the CLI command snippet shown**

---

#### 💻 JavaScript Project Analysis

1. **Clone your JavaScript project**
   ```bash
   git clone https://github.com/<your-js-repo>.git
   cd react-course-part1
   ```

2. **Install Node.js dependencies**
   ```bash
   sudo apt install npm
   npm install
   npm run build
   ```

3. **Install SonarScanner**
   ```bash
   npm install -g @sonar/scan
   ```

4. **Create and edit the `sonar-project.properties` file**
   ```bash
   vi sonar-project.properties
   ```

   **Add the following content:**
   ```
   sonar.projectKey=js
   sonar.projectName=js
   sonar.projectVersion=1.0
   sonar.sources=.
   sonar.host.url=http://<ec2_publicip>:9000
   sonar.login=sqp_<generated_token>
   ```

5. **Run SonarQube analysis**
   ```bash
   sonar-scanner
   ```

---
![](./images/sonar%20analysis%20output.png)

#### ✅ Final Notes

- Ensure your EC2 security group allows inbound access to port `9000`.
- Make sure Node.js and npm are properly installed on your server.
- Review analysis results in the SonarQube web dashboard.
