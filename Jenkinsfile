 
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
                    mkdir -p $WORKSPACE/deploy
                    cp index.html $WORKSPACE/deploy/
                '''
                echo "Deployment copied to EC2 workspace folder."
            }
        }
    }
}
