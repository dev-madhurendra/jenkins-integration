pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/dev-madhurendra/jenkins-integration-with-github.git']]])
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
