# Installing-SonarQube
Installing SonarQube on local machine via docker container and also setting up with Jenkins.

1. Run the docker container for SonarQube Community Edition.
docker run -d -p 9000:9000 sonarqube:community

2. Install the SonarQube Scanner plugin in Jenkins.
Go to Jenkins (localhost:8080) -> Manage Jenkins -> Plugins -> Available Plugins -> SonarQube Scanner -> Install

3. Generate Token in Sonarqube
Go to Sonarqube (localhost:9000) -> My Account (top Right) -> Security
Give a name, select User, select 30 days and Generate token. Copy the generated token
SonarQube Token Generated![image](https://github.com/user-attachments/assets/0158bf62-72fc-43bf-969c-036e7195e51f)

5. Add Sonarqube token in Jenkins for authentication
Go to Jenkins (localhost:8080) -> Manage Jenkins -> Credentials -> System -> Global -> Add Credentials
Select Secret text and add the copied sonarqube token in Secret.
![image](https://github.com/user-attachments/assets/82ef5aeb-3d8b-4231-9b4c-5c02be1d293f)

6. Add SonarQube Server in Jenkins Configuration
Go to Jenkins (localhost:8080) -> Manage Jenkins -> System -> SonarQube Servers
Enter Name(SonarServer), Url(localhost:9000), select Server Authentication Token(sonarqube)
![image](https://github.com/user-attachments/assets/0bdaf031-a1cb-48aa-b084-ce921a857621)

7. Add Maven in Jenkins Configuration
Go to Jenkins (localhost:8080) -> Manage Jenkins -> Tools -> Maven Installations
![image](https://github.com/user-attachments/assets/54f1bae2-bb9d-4066-8b70-238ec49e9228)

8. Configure the JenkinsFile to Test SonarQube



SonarQube Account![image](https://github.com/user-attachments/assets/63c426fe-fa3e-44ea-a53e-8839935327e6)
SonarQube Token Generated![image](https://github.com/user-attachments/assets/0158bf62-72fc-43bf-969c-036e7195e51f)
SonarQube Token Add in Jenkins ![image](https://github.com/user-attachments/assets/82ef5aeb-3d8b-4231-9b4c-5c02be1d293f)
SonarQube Server Jenkins Configuration


