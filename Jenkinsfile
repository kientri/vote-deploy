pipeline {

    agent any
 
    stages {
        stage('Update GIT') {
            steps {
                echo 'inside deployment'
                
                script {
                        sh "cat vote-ui-deployment.yaml"
                }
            }
        }
    }     
}
