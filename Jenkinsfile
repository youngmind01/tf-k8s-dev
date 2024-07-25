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
                    echo "DEBUG: REMOTE_HOST = ${REMOTE_HOST}"
                    echo "DEBUG: SSH_CREDENTIALS = ${SSH_CREDENTIALS}"

                    def remoteCmd = "echo Hello from Jenkins"
                    def sshCommand = "ssh -o StrictHostKeyChecking=no -i ${SSH_CREDENTIALS} mylab@${REMOTE_HOST} '${remoteCmd}'"
                    echo "DEBUG: sshCommand = ${sshCommand}"

                    sh(script: sshCommand, returnStdout: true)
                }
            }
        }
    }
}