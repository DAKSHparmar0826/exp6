pipeline {
    agent any

    tools {
    maven 'Maven3'
    jdk 'JDK17'
}


    stages {

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',
                        path: '',
                        url: 'http://localhost:8081'
                    )
                ],
                contextPath: 'exp6',
                war: '**/*.war'
            }
        }

    }
}
