pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-token', url: 'https://github.com/VazirJamilCodeCraft/autodeploy.git'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "Copying index.html to NGINX web root..."
                    sudo cp index.html /var/www/html/index.html
                    echo "Deployment successful!"
                '''
            }
        }
    }
}
