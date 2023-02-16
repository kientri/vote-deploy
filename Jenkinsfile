pipeline {

    agent any
 
    stages {
        stage('Update GIT') {
            steps {
                echo 'inside deployment'
                
                script {
                    catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                        withCredentials([usernamePassword(credentialsId: 'github-authen-token', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                            sh "git config user.email tonyaom@gmail.com"
                            sh "git config user.name Tony"
                            sh "cat vote-ui-deployment.yaml"
                            sh "sed -i 's+tonyaom/vote.*+tonyaom/vote:${DOCKERTAG}+g' vote-ui-deployment.yaml"
                            sh "cat vote-ui-deployment.yaml"
                            sh "git add ."
                            sh "git commit -m 'Done by Jenkins Job deployment: ${env.BUILD_NUMBER}'"
                            sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/vote-deploy.git HEAD:master"
                        }
                    }
                }
            }
        }
    }     
}
