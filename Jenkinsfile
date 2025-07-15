pipeline {
    agent any

    stages {
        stage('Create Virtual Environment') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
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
                sh '''
                    echo "Deployment step (simulated)"
                '''
            }
        }
    }
}
