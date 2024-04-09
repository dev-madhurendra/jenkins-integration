pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the repository
                git 'https://github.com/dev-madhurendra/jenkins-integration-with-github.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Install project dependencies using pip
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Run Tests') {
            steps {
                // Run unit tests
                sh 'python -m unittest tests/test_main.py'
            }
        }
        
        stage('Run Main Script') {
            steps {
                // Run the main Python script
                sh 'python src/main.py'
            }
        }
    }
    
    post {
        always {
            // Archive test results
            junit 'tests/**/*.xml'
        }
    }
}
