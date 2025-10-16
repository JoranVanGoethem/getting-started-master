node {
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop getting-started'
            sh 'docker rm getting-started'
        }
    }
    stage('Build') {
        build 'BuildGettingStartedApp'
    }
    stage('Results') {
        build 'TestGettingStartedApp'
    }
}