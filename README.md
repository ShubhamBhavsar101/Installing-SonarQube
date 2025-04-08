
# 🚀 Installing SonarQube with Jenkins Integration

This guide walks you through installing **SonarQube** on your local machine using Docker 🐳, integrating it with **Jenkins** 🧩, and running your first build with **SonarQube analysis** 📊.

---

## 🔧 1. Run the SonarQube Docker Container

```bash
docker run -d -p 9000:9000 sonarqube:community
```

> 🔎 This pulls and runs the SonarQube Community Edition container on port 9000.

---

## 📦 2. Install SonarQube Scanner Plugin in Jenkins

1. Go to Jenkins: [http://localhost:8080](http://localhost:8080)
2. Navigate to: **Manage Jenkins** → **Plugins** → **Available Plugins**
3. Search for **SonarQube Scanner** and click **Install**.

---

## 🔐 3. Generate Token in SonarQube

1. Visit SonarQube: [http://localhost:9000](http://localhost:9000)
2. Click **My Account** (top-right) → **Security**
3. Provide a name, set expiration (e.g., 30 days), and click **Generate Token**
4. **Copy the token** 📋 (you’ll need it in the next steps!)

After generating the token, you should see a screen like this:

![SonarQube Token Generated](https://github.com/user-attachments/assets/fbe29c17-d274-4e0e-b079-738805e6033f)

> 📌 **Note:** Make sure to copy and store the token securely. You won’t be able to see it again after closing the window.


---

## 🔑 4. Add SonarQube Token in Jenkins

1. Go to Jenkins → **Manage Jenkins** → **Credentials** → **System** → **Global** → **Add Credentials**
2. Choose **Secret text**
3. Paste the token you copied in the **Secret** field

![SonarQube Token Jenkins](https://github.com/user-attachments/assets/82ef5aeb-3d8b-4231-9b4c-5c02be1d293f)

> ✅ This allows Jenkins to authenticate with SonarQube.

---

## 🌐 5. Configure SonarQube Server in Jenkins

1. Navigate to: **Manage Jenkins** → **System** → **SonarQube Servers**
2. Click **Add SonarQube**
3. Fill in:
   - **Name**: `SonarServer`
   - **Server URL**: `http://localhost:9000`
   - **Server Authentication Token**: Select the token you added earlier

![SonarServer Jenkins](https://github.com/user-attachments/assets/0bdaf031-a1cb-48aa-b084-ce921a857621)

---

## 🛠️ 6. Add Maven in Jenkins Configuration

1. Go to **Manage Jenkins** → **Global Tool Configuration** → **Maven**
2. Click **Add Maven**
3. Provide a name and install it automatically or point to an existing Maven installation

![Maven Tools](https://github.com/user-attachments/assets/54f1bae2-bb9d-4066-8b70-238ec49e9228)

> 🧰 Maven is required to build and analyze Java projects.

---

## 📄 7. Configure Jenkins Project for SonarQube

1. Go to Jenkins -> New Item
2. Enter name as "SonarQube Test", Select Pipeline, Create Project
3. Go to Pipeline and add the Jenkinsfile contents from this repository into the Pipeline script.
4. Click on Save.
---

## ✅ 8. Run the Build

1. Click **Build Now** 🛠️
2. Watch the console output for progress
3. Visit SonarQube to see the results 🎯

- Build status will be **SUCCESS** ✅
- Code quality metrics will be available on your SonarQube dashboard at: [http://localhost:9000](http://localhost:9000)

![Build is Success](https://github.com/user-attachments/assets/6972dbb2-aae2-4597-a345-a4e63ef50d6b)
---


## 📝 Notes

- Ensure **Docker** and **Jenkins** are installed and running on your machine
---

