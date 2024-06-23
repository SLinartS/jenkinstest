pipeline {
    agent any

    options {
      timestamps()
      disableConcurrentBuilds(abortPrevious: true)
    }

    triggers { pollSCM('* * * * *') }

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
                sh 'npx kill-port 9000'
                sh 'node ./server.js'
            }
        }
    }
}