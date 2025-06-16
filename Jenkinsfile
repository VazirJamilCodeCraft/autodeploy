pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-token', url: 'https://github.com/VazirJamilCodeCraft/autodeploy.git'
            }
        }
        stage('Deploy to Apache') {
            steps {
                sh '''
                    sudo cp index.html /var/www/html/index.html
                    echo "Deployed to Apache document root"
                '''
            }
        }
    }
}
