pipeline {
    agent any

    tools {
        maven 'Maven 3.8.7' // Set this up in Jenkins → Global Tool Config
        jdk 'Java 21'       // Set this in Jenkins → Global Tool Config
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add your deploy logic here (e.g. copying JAR, running java -jar)
                sh 'nohup java -jar target/*.jar &'
            }
        }
    }

    post {
        success {
            mail to: 'janhvidahake2001@gmail.com',
                 subject: "SUCCESS: Build #${env.BUILD_NUMBER}",
                 body: "Good job! Spring Boot build succeeded."
        }
        failure {
            mail to: 'janhvidahake2001@gmail.com',
                 subject: "FAILURE: Build #${env.BUILD_NUMBER}",
                 body: "Oops! The build failed."
        }
    }
}


