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
        // Gebruik je bestaande Freestyle job
        build job: 'BuildGettingStartedApp', wait: true, propagate: true
      }
    }

    stage('Results') {
      steps {
        // Gebruik je bestaande Test job
        build job: 'TestGettingStartedApp', wait: true, propagate: true
      }
    }
  }   
}

// test