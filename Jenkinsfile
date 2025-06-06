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
                mkdir -p /var/www/html/
                cp index.html /var/www/html/
                '''
            }
        }
    }
}
