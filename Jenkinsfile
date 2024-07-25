pipeline {
    agent any
    
    stages {
        stage('checkout') {
            steps {
                git credentialsId: '02', url: 'https://github.com/youngmind01/tf-k8s-dev.git'
            }
        }

        stage('terraform init') {
            steps {
                script {
                    sh """
                    cd tf-k8s-dev
                    terraform init
                    """
                }
            }
        }
    }
}