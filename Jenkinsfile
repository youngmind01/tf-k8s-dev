pipeline {
    agent any

    stages {
        stage('SSH Command') {
            steps {
                script {
                    // Disable strict host key checking (not recommended for production)
                    sh 'ssh -o StrictHostKeyChecking=no mylab@192.168.150.132 echo Hello from Jenkins'
                }
            }
        }
    }
}