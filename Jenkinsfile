pipeline {
    agent any

    environment {
        PYENV_ROOT = "$HOME/.pyenv"
    }

    stages {
        stage('Set Up Python and Venv') {
            steps {
                sh '''
                    # Set up pyenv and activate virtualenv inside the Jenkins workspace
                    export PYENV_ROOT="$HOME/.pyenv"
                    export PATH="$PYENV_ROOT/bin:$PATH"
                    eval "$(pyenv init --path)"
                    eval "$(pyenv init -)"
                    eval "$(pyenv virtualenv-init -)"

                    pyenv shell 3.10.13
                    pyenv virtualenv 3.10.13 cicdvenv || true
                    pyenv activate cicdvenv

                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    export PYENV_ROOT="$HOME/.pyenv"
                    export PATH="$PYENV_ROOT/bin:$PATH"
                    eval "$(pyenv init --path)"
                    eval "$(pyenv init -)"
                    eval "$(pyenv virtualenv-init -)"
                    pyenv activate cicdvenv

                    pytest
                '''
            }
        }

        stage('Deploy (Simulated)') {
            steps {
                sh '''
                    echo "Simulating deployment..."
                '''
            }
        }
    }
}
