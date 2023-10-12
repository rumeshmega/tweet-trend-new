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
                 echo "-------------build Started--------"
                sh 'mvn clean deploy -Dmaven.test.skip-true'
                 echo "-------------build Completed-------"
            }
        }
        stage("test") {
            steps {
                 echo "-------------Unit test Started--------"
                sh 'mvn surefire-report:report'
                 echo "-------------Unit test Completed-------"
            }
        }

    stage('SonarQube analysis') {
    environment {
      scannerHome = tool 'rumesh-scanner'
    }
    steps{
    withSonarQubeEnv('rumesh-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }


    }
}

    

  