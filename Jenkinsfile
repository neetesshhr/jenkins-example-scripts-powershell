pipeline {
  agent any
  stages {
    stage('version') {
      steps {
        sh 'pwsh --version'
      }
    }
    stage('hello') {
      steps {
        sh 'pwsh hello.ps1'
      }
    }
  }
  post {
    always {
      emailext subject: "Pipeline ${currentBuild.result}: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                body: "${env.BUILD_URL}",
                recipientProviders: [[$class: 'EditableEmailRecipientProvider', 
                                     recipients: 'rijalnitesh78@gmail.com']],
                replyTo: "\${DEFAULT_REPLYTO}",
                mimeType: 'text/html',
                attachLog: true
    }
  }
}
