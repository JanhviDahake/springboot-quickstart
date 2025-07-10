pipeline {
    agent any

    tools {
        maven 'Maven 3.8.7'   // Use the Maven installed in Jenkins (name from Global Tool Config)
        jdk 'JDK 21'          // Use Java 11 or your desired version
    }

    environment {
        APP_NAME = 'springboot-quickstart'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/JanhviDahake/springboot-quickstart.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Spring Boot app...'
                // Example: move to deployment folder, run jar, upload to S3, etc.
                sh 'cp target/*.jar deploy/'
            }
        }
    }

    post {
        success {
            echo '🎉 Build and deploy succeeded!'
            mail to: 'janhvidahake2001@gmail.com',
                 subject: "Jenkins Build Success: ${APP_NAME}",
                 body: "Build and deploy completed successfully."
        }

        failure {
            echo '❌ Build failed.'
            mail to: 'janhvidahake2001@gmail.com',
                 subject: "Jenkins Build Failed: ${APP_NAME}",
                 body: "The build or tests failed. Please check Jenkins."
        }
    }
}

