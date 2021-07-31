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
      steps {
        git 'https://github.com/nikola-bodrozic/katalon.git'
        sh "docker run -t --rm -v "\$(pwd)":/tmp/project katalonstudio/katalon katalonc.sh -projectPath=/tmp/project -browserType=\"Chrome\" -retry=0 -statusDelay=15 -testSuitePath=\"Test Suites/login\" -apikey=${KATALON_API_KEY}'
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
