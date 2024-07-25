pipeline {
    agent any
    
    environment {
        REMOTE_HOST = '192.168.150.132' 
        SSH_CREDENTIALS = '01'  // Update this to your actual SSH credentials ID
    }
    
    stages {
        stage('checkout') {
            steps {
                git credentialsId: '02', url: 'https://github.com/youngmind01/tf-k8s-dev.git'
            }
        }

        stage('remote-ssh') {
            environment {
                SSH_USER = credentials(env.SSH_CREDENTIALS).username  // Correct usage of credentials function
                SSH_PASS = credentials(env.SSH_CREDENTIALS).password  // Correct usage of credentials function
            }
            steps {
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