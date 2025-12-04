pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/yourname/web-demo.git'
            }
        }

        stage('Deploy to App Server') {
            steps {
                sshagent(credentials: ['appserver-key']) {
                    sh '''
                        echo "Copying index.html to Application Server..."
                        scp index.html ubuntu@APP_SERVER_IP:/var/www/html/index.html
                    '''
                }
            }
        }
    }

    post {
        success {
            echo "Deployment successful!"
        }
        failure {
            echo "Deployment failed!"
        }
    }
}

