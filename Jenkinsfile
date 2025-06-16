pipeline {
    agent any

    environment {
        DEPLOY_PATH = "/var/www/html"
        FILE_NAME = "index.html"
    }

    stages {

        stage('Checkout Source') {
            steps {
                echo "📥 Cloning repository..."
                git credentialsId: 'github-token', url: 'https://github.com/VazirJamilCodeCraft/autodeploy.git', branch: 'main'
            }
        }

        stage('Build Summary') {
            steps {
                echo "📝 Build Info"
                sh '''
                    echo "Workspace Files:"
                    ls -la
                    echo "File Preview (first 10 lines):"
                    head -n 10 index.html
                '''
            }
        }

        stage('Deploy to Apache') {
            steps {
                echo "🚀 Deploying to Apache..."

                // Use sudo with no password prompt
                sh '''
                    if [ ! -f "${FILE_NAME}" ]; then
                        echo "❌ Error: ${FILE_NAME} not found!"
                        exit 1
                    fi

                    echo "🛠 Copying ${FILE_NAME} to ${DEPLOY_PATH}"
                    sudo /bin/cp ${FILE_NAME} ${DEPLOY_PATH}/${FILE_NAME}
                    echo "✅ Successfully deployed ${FILE_NAME} to ${DEPLOY_PATH}"
                '''
            }
        }

        stage('Post Deployment Check') {
            steps {
                echo "🔍 Verifying deployed content..."
                sh '''
                    echo "Current index.html on Apache:"
                    head -n 10 ${DEPLOY_PATH}/index.html
                '''
            }
        }
    }

    post {
        success {
            echo "🎉 Deployment successful! Visit: http://13.60.236.53/"
        }
        failure {
            echo "❌ Deployment failed! Check logs and permissions."
        }
    }
}
