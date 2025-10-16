node {
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop beautiful_proskuriakova'
            sh 'docker rm beautiful_proskuriakova'
        }
    }
    stage('Build') {
        build 'BuildGettingStartedApp'
    }
    stage('Results') {
        build 'TestGettingStartedApp'
    }
}