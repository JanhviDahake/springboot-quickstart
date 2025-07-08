pipeline {
    agent any

    tools {
        maven 'Maven 3'    // Define this in Jenkins Global Tool Config
        jdk 'JDK 21'       // Also define in Global Tool Config
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/JanhviDahake/springboot-quickstart.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the Spring Boot app'
                sh 'mvn clean package'
            }
