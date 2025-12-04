pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/aryapillai/devops'
            }
        }

        stage('Deploy to App Server') {
            steps {
                sshagent(credentials: ['appserver-key']) {
                    sh '''
                        echo "Copying index.html to Application Server..."
                        scp index.html ubuntu@13.239.122.121:/var/www/html/index.html
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

