pipeline {
  agent any

  tools {
    maven 'Maven 3.8.7'
    jdk 'JDK 21'
  }

  stages {
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
        echo 'Deploying to staging...'
        sh 'cp target/*.jar /home/ubuntu/deploy/'
      }
    }
  }

  post {
    success {
      mail to: 'janhvidahake2001@gmail.com',
           subject: 'Build Success',
           body: 'The Jenkins build succeeded.'
    }
    failure {
      mail to: 'janhvidahake2001@gmail.com',
           subject: 'Build Failed',
           body: 'The Jenkins build failed.'
    }
  }
}
