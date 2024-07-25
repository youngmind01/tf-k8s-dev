pipeline {
    agent any

    environment {
        KUBE_NODE_IP = '192.168.150.132'
    }
    
    stages {
        stage('checkout') {
            steps {
                git credentialsId: '02', url: 'https://github.com/youngmind01/tf-k8s-dev.git'
            }
        }

        stage('cluster-connect') {
            steps {
                script {
                    def creds = credentials('01')
                    if (creds == null) {
                        error "Credentials with ID '01' not found"
                    }
                    sh """
                    sshpass -p '${creds.password}' ssh '${creds.username}@${env.KUBE_NODE_IP}' 'kubectl get pods -A'
                    """
                }
            }
        }
    }
}