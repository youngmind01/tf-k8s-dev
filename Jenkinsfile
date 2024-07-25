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
                    def creds = credentials(SSH_CREDENTIALS)
                    SSH_USER = creds.username
                    SSH_PASS = creds.password
                    
                    // SSH into the remote host using password authentication
                    sshCommand remote: [
                        host: REMOTE_HOST,
                        user: SSH_USER,
                        password: SSH_PASS,
                        port: 22  
                    ]
                }
            }
        }
    }
}