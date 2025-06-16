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
                    echo "Deploying index.html to Apache root..."
                    sudo /bin/cp index.html /var/www/html/index.html
                    echo "Deployment done ✅"
                '''
            }
        }
    }
}
