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
    stage('Deploy') {
        sh './jenkins/scripts/deliver.sh'
        #input message: 'Finished using the web site? (Click "Proceed" to continue)'
        sleep 60
        sh './jenkins/scripts/kill.sh'
    }
  }
 }
}
