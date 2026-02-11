pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK17'
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/DAKSHparmar0826/exp6.git'
            }
        }

        stage('Build Project') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-credentials',
                        path: '',
                        url: 'http://localhost:8081'
                    )
                ],
                contextPath: 'demoapp',
                war: '**/*.war'
            }
        }
    }
}
