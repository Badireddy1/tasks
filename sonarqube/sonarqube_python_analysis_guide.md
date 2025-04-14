
### 📘 SonarQube Setup and Python Project Analysis Guide

#### 🚀 Configure SonarQube for Python Project

1. **Go to Projects → Create Project**

2. **Choose `Local` Project**

3. **Provide Project Details**
   - Project Key: `python`
   - Project Name: `python`

4. **Choose Configuration**
   - Select `Use global settings`
   - Then choose `Locally`

5. **Generate Authentication Token**
   - Click on `Generate`
   - Copy the generated token
   - Click `Continue`

6. **Copy the CLI command snippet shown**

---

#### 💻 Python Project Analysis

1. **Clone your Python project**
   ```bash
   git clone https://github.com/<your-python-repo>.git
   cd FindTheBank
   ```

2. **Ensure `.py` files are present**

3. **Run SonarQube analysis**
   ```bash
   sonar-scanner \
     -Dsonar.projectKey=python \
     -Dsonar.sources=. \
     -Dsonar.host.url=http://<ec2_publicip>:9000 \
     -Dsonar.token=sqp_<generatedtoken>
   ```

---
![](./images/sonar%20analysis%20output.png)
#### ✅ Final Notes

- Ensure your EC2 security group allows inbound access to port `9000`.
- Make sure `sonar-scanner` is installed and available in the PATH.
- Review analysis results in the SonarQube web dashboard.
