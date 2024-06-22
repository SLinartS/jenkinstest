pipeline {
    agent any

    stages {
        stage('Build') { 
            steps {
              nodejs(
                sh 'npm install' 
                sh 'npm run build'
              )
            }
        }
        stage('Deliver') { 
            steps {
                sh 'node ./server.js' 
            }
        }
    }
}