properties([disableConcurrentBuilds()])

pipeline {
    agent any

    options {
      timestamps()
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
                sh 'JENKINS_NODE_COOKIE=dontKillMe nohup node ./server.js &'
            }
        }
    }
}