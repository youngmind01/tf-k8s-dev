pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: '02', url: 'https://github.com/youngmind01/tf-k8s-dev.git'
            }
        }
        stage('SSH Command') {
            steps {
                script {
                    // Execute SSH command and then execute a remote command
                    sh "ssh mylab@192.168.150.132 'echo Hello from Jenkins'"
                }
            }
        }
    }
}