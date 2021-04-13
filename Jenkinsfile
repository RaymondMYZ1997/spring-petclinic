pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn install'
      }
    }

    stage('StaticAnalysis') {
      steps {
        sh 'mvn sonar:sonar -Dsonar.projectKey=org.springframework.samples:spring-petclinic -Dsonar.host.url=http://127.0.0.1:9000 -Dsonar.login=072d22f58ff1f9991945488e9bf3495179ce0d1b'
      }
    }

    stage('Deploy') {
      steps {
        sh '''cp /home/vagrant/deployment.yml ./deployment-playbook.yml && cp /home/vagrant/Dockerfile ./ && ansible-playbook --user=vagrant deployment-playbook.yml ; rm deployment-playbook.yml ; rm Dockerfile
'''
      }
    }

  }
}