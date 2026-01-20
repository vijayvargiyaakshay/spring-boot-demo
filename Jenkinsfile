pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/vijayvargiyaakshay/spring-boot-demo.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                echo Stopping old app (if running)
                taskkill /F /IM java.exe /T || echo No running app

                echo Starting Spring Boot app
                start "" java -jar target\\*.jar
                '''
            }
        }
    }
}
