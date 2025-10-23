properties([pipelineTriggers([pollSCM('* * * * *')])])

pipeline {
  agent any
  stages {
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop gettingstartedapp'
            sh 'docker rm gettingstartedapp'
        }
    }
    stage('Build') {
        build 'BuildGettingStartedApp'
    }
    stage('Results') {
        build 'TestGettingStartedApp'
    }
  }
}

// test