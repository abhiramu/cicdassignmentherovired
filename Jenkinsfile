pipeline {
    agent any

    environment {
        PROJECT_DIR = "/home/ubuntu/projectFolder1"
        PYENV_ROOT = "$HOME/.pyenv"
    }

    stages {
        stage('Activate Pyenv and Install Dependencies') {
            steps {
                sh '''
                    # Go to the project folder where pyenv is initialized
                    cd $PROJECT_DIR

                    # Set up pyenv environment for this shell
                    export PYENV_ROOT="$HOME/.pyenv"
                    export PATH="$PYENV_ROOT/bin:$PATH"
                    eval "$(pyenv init --path)"
                    eval "$(pyenv init -)"
                    eval "$(pyenv virtualenv-init -)"

                    # Activate the local pyenv version (assumes it was set using pyenv local)
                    pyenv activate $(cat .python-version)

                    # Install requirements
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    cd $PROJECT_DIR

                    export PYENV_ROOT="$HOME/.pyenv"
                    export PATH="$PYENV_ROOT/bin:$PATH"
                    eval "$(pyenv init --path)"
                    eval "$(pyenv init -)"
                    eval "$(pyenv virtualenv-init -)"

                    pyenv activate $(cat .python-version)

                    pytest
                '''
            }
        }

        stage('Deploy (Simulated)') {
            steps {
                sh '''
                    cd $PROJECT_DIR
                    echo "Deployment step (simulated)..."
                '''
            }
        }
    }
}
