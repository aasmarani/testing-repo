pipeline {
  agent {
    node {
      label 'jslave'
    }
    
  }
  stages {
    stage('Build') {
      steps {
        echo 'testing create pipeline'
        git(url: 'https://gitlabin.bajau.com/aasmarani/reflex.git', credentialsId: 'gitlabcred')
        libraryResource 'library-bajau'
      }
    }
    stage('Testing') {
      steps {
        parallel(
          "Testing": {
            sh 'echo "manual testing"'
            
          },
          "Security": {
            sh 'echo "execute security tools"'
            
          }
        )
      }
    }
    stage('Release') {
      steps {
        echo 'release !'
      }
    }
  }
  environment {
    mailDeveloper = 'aasmarani@bajau.com; nrini@bajau.com'
    gitlabHostname = 'gitlabin.bajau.com'
    jenkinsHostname = '172.17.0.10'
  }
}