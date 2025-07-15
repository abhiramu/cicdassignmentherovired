pipeline {
    agent any

    stages {
        stage('Create Virtual Environment') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    . venv/bin/activate
                    pytest
                '''
            }
        }

        stage('Deploy (Simulated)') {
            steps {
                sh 'echo "Simulating deployment..."'
            }
        }
    }

    post {
        success {
            emailext (
                to: 'yourgmail@gmail.com',
                subject: "✅ Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins build completed successfully.\n\nJob: ${env.JOB_NAME}\nBuild URL: ${env.BUILD_URL}"
            )
        }

        failure {
            emailext (
                to: 'yourgmail@gmail.com',
                subject: "❌ Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins build has failed.\n\nJob: ${env.JOB_NAME}\nBuild URL: ${env.BUILD_URL}"
            )
        }
    }
}
