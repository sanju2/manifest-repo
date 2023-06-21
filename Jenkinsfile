node {
    def app

    stage('Clone Repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh "git config user.email lsanjeewa947@gmail.com"
                        sh "git config user.name Sanju2"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+lasanthasanjeewa/test.*+lasanthasanjeewa/test:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/GitOps_ArgoCD_Jenkins_K8S_files.git HEAD:main"
      }
    }
  }
}
}
