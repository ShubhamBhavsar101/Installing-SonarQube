pipeline {
    agent any
    
    environment {
        SONARQUBE_ENV = 'SonarServer'
    }
    
    tools {
        maven 'Maven'
    }
    
    stages {
        stage('Checkout') {
          steps {
            git branch: 'main', url: 'https://github.com/ShubhamBhavsar101/Jenkins-Zero-To-Hero.git'
          }
        }
        stage('Build') {
          steps {
            // build the project and create a JAR file
            sh 'cd java-maven-sonar-argocd-helm-k8s/spring-boot-app && mvn clean package'
          }
        }
        
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${env.SONARQUBE_ENV}") {
                    sh 'cd java-maven-sonar-argocd-helm-k8s/spring-boot-app && mvn sonar:sonar'
                }
            }
        }
    }
}
