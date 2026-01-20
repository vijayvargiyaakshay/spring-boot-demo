pipeline {
    agent any

    tools {
        jdk 'JDK17'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/vijayvargiyaakshay/spring-boot-demo.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvnw.cmd clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvnw.cmd test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvnw.cmd clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                taskkill /F /IM java.exe /T || echo No running app
                start "" java -jar target\\*.jar
                '''
            }
        }
    }
}
