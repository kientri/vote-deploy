pipeline {

    agent any
 
    stages {
        stage('Update GIT') {
            steps {
                echo 'inside deployment'
                
                script {
                    catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                        sh "cat vote-ui-deployment.yaml"
                    }
                }
            }
        }
    }     
}
