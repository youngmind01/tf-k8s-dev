pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('SSH Command') {
            steps {
                script {
                    // Example of using sshCommand
                    sshCommand remote: '192.168.150.132', command: 'echo Hello from Jenkins'
                }
            }
        }
    }
}