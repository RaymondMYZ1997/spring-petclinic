pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn install'
      }
    }

    stage('Test') {
      steps {
        sh '''mvn sonar:sonar \\
>   -Dsonar.projectKey=org.springframework.samples:spring-petclinic \\
>   -Dsonar.host.url=http://127.0.0.1:9000 \\
>   -Dsonar.login=c2c6f60b505e6a58c6e9b1a3d9db70f0f656152a'''
      }
    }

    stage('Deploy') {
      steps {
        sh 'java -jar target/*.jar '
      }
    }

  }
}