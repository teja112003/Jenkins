pipeline {
    agent any
    
    environment {
        VENV_DIR = 'venv'
    }
    
    stages {
        stage('Checkout SCM') {
            steps {
                echo "Cloning the repository..."
                git branch: 'main', url: 'https://github.com/mvsanthi123/jenkins.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh '''
                    python3 -m venv ${VENV_DIR}
                    . ${VENV_DIR}/bin/activate
                    python3 -m pip install --upgrade pip
                    python3 -m pip install -r requirements
                '''
            }
        }

     
        stage('Extract Data from app.py and Display Output') {
    steps {
        script {
            // This will now correctly import get_output from app.py and print it
            sh 'python3 -c "from app import get_output; print(get_output())"'
        }
    }
}
    }
}
