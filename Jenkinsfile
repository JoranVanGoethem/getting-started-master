properties([pipelineTriggers([pollSCM('* * * * *')])])

pipeline {
  agent any
   stages {
    stage('Preparation') {
      steps {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop gettingstartedapp'
            sh 'docker rm gettingstartedapp'
        }
      }
    }

    stage('Build') {
      steps {
        build job: 'BuildGettingStartedApp', wait: true, propagate: true
      }
    }

    stage('Results') {
      steps {
        build job: 'TestGettingStartedApp', wait: true, propagate: true
      }
    }
  }   
}

// test