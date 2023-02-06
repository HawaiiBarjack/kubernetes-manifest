node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }
    
    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email 382844615@qq.com"
                        sh "git config user.name hawaiibarjack"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i '' 's+barjack/devops-learning.*+barjack/devops-learning:${env.BUILD_NUMBER}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Triggered Build: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetes-manifest.git HEAD:main"
      }
    }
  }
}
}
