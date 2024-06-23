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
                sh 'lsof -ti tcp:9000 && lsof -ti tcp:9000 | xargs kill'
                sh 'nohup node ./server.js &'
            }
        }
    }
}