pipeline {
  agent any
  stages {
<<<<<<< HEAD
    stage('git pull') {
      steps {
        // https://github.com/Modney/GitOps.git will replace by sed command before RUN
=======
    stage('Deploy start') {
      steps {
        slackSend(message: "Deploy ${env.BUILD_NUMBER} Started"
        , color: 'good', tokenCredentialId: 'slack-key')
      }
    }      
    stage('git pull') {
      steps {
        // Git-URL will replace by sed command before RUN
>>>>>>> 0a36a0bbb5342f971db50850ab8723f8f7077dfc
        git url: 'https://github.com/Modney/GitOps.git', branch: 'main'
      }
    }
    stage('k8s deploy'){
      steps {
        kubernetesDeploy(kubeconfigId: 'kubeconfig',
                         configs: '*.yaml')
      }
<<<<<<< HEAD
    }    
  }
}
=======
    }
    stage('send diff') {
      steps {
        script {
          def publisher = LastChanges.getLastChangesPublisher "PREVIOUS_REVISION", "SIDE", "LINE", true, true, "", "", "", "", ""
          publisher.publishLastChanges()
          def htmlDiff = publisher.getHtmlDiff()
          writeFile file: "deploy-diff-${env.BUILD_NUMBER}.html", text: htmlDiff
        }
        slackSend(message: """${env.JOB_NAME} #${env.BUILD_NUMBER} End
        (<${env.BUILD_URL}/last-changes|Check Last changed>)"""
        , color: 'good', tokenCredentialId: 'slack-key')             
      }
    }
  }
}
>>>>>>> 0a36a0bbb5342f971db50850ab8723f8f7077dfc
