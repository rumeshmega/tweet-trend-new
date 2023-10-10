pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.4/bin:$PATH"
}

    stages {
        stage("build") {
            steps {
                sh 'mvn clean deploy'
            }
        }

    stage('Sonarqube') {
    environment {
        scannerHome = tool 'rumesh-scanner'
    }
    steps {
        withSonarQubeEnv('rumesh-sonarqube-server') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
    }
  }
}    
}
  
