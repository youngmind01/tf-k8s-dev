pipeline {
    agent any

    environment {
        REMOTE_HOST = '192.168.150.132'
        SSH_CREDENTIALS = credentials('01') 
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: '02', url: 'https://github.com/youngmind01/tf-k8s-dev.git'
            }
        }
        stage('SSH Command') {
            steps {
                script {
                    def remoteCmd = "echo Hello from Jenkins"
                    sh remoteUser: 'mylab', remoteHost: REMOTE_HOST, credentialsId: SSH_CREDENTIALS, command: remoteCmd
                }
            }
        }
    }
}