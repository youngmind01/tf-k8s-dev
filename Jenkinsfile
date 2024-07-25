pipeline {
    agent any
    
    environment {
        REMOTE_HOST = '192.168.150.132' 
        SSH_CREDENTIALS = '01'  // Update this to your actual SSH credentials ID
        SSH_USER = ''
        SSH_PASS = ''
    }
    
    stages {
        stage('checkout') {
            steps {
                git credentialsId: '02', url: 'https://github.com/youngmind01/tf-k8s-dev.git'
            }
        }

        stage('remote-ssh') {
            steps {
                withCredentials([usernamePassword(credentialsId: "${SSH_CREDENTIALS}", usernameVariable: 'SSH_USER', passwordVariable: 'SSH_PASS')]) {
                    script {
                        // SSH into the remote host using password authentication
                        sshCommand remote: [
                            host: env.REMOTE_HOST,
                            user: env.SSH_USER,
                            password: env.SSH_PASS,
                            port: 22  
                        ]
                    }
                }
            }
        }
    }
}