pipeline {
    agent any
    
    environment {
        REMOTE_HOST = '192.168.150.132' 
        SSH_CREDENTIALS = '01'  // Update this to your actual SSH credentials ID
        SSH_USER = ''  // Initialize variables for later use
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
                script {
                    // Retrieve SSH credentials dynamically
                    def credentials = credentials(env.SSH_CREDENTIALS)
                    SSH_USER = credentials.username
                    SSH_PASS = credentials.password
                    
                    // SSH into the remote host using password authentication
                    sshCommand remote: [
                        host: env.REMOTE_HOST,
                        user: SSH_USER,
                        password: SSH_PASS,
                        port: 22  
                    ]
                }
            }
        }
    }
}