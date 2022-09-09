node {
    checkout scm
    withEnv(['CI=true']) {
    docker.image('node:lts-buster-slim').inside('-p 3000:3000') {
    stage('Build') {
        sh 'npm install'
    }
    stage('Test') {
        sh './jenkins/scripts/test.sh'
    }
    stage('Manual Approval') {
       input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
    }
    stage('Deploy') {
        sh './jenkins/scripts/deliver.sh'
        sh 'sleep 60'
        sh './jenkins/scripts/kill.sh'
    }
  }
 }
}
