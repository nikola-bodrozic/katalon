pipeline {
  agent {
    docker {
      image 'katalonstudio/katalon'
      args "-u root"
    }
  }

  environment {
     KATALON_API_KEY = credentials('4bdfb4e8-80ff-4ade-ac99-564697fb4b1e')
  }
  
  stages {
    stage('Test') {
      agent {
        docker {
           image 'katalonstudio/katalon'
            args "-u root"
        }
      }
      steps {
        git 'https://github.com/nikola-bodrozic/katalon.git'
        sh 'ls -lA'
        sh 'katalonc.sh -browserType="Chrome" -retry=0 -statusDelay=15 -testSuitePath="Test Suites/login" -projectPath=. -apikey=${KATALON_API_KEY}'
      }
    }
  }
  post {
    success {
      echo 'test passed'
    }
    always {
      deleteDir()
    }
    failure {
      echo 'send warning about broken build'
    }
  }
}
