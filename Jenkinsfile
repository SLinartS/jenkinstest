properties([disableConcurrentBuilds()])

pipeline {
    agent {
      label 'main'
    }

    options {
      timestamps()
    }

    triggers { pollSCM('*****') }

    tools {
      nodejs 'node'
    }

    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Deliver') { 
            steps {
                sh 'npm run build'
            }
        }
        stage('Run') { 
            steps {
                sh 'node ./server.js'
            }
        }
    }
}