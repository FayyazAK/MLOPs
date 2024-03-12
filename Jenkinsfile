pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install dependencies') {
            steps {
                script {
                    sh 'pip install -r requirements.txt'
                }
            }
        }
        
        stage('Run tests') {
            steps {
                script {
                    sh 'pytest test.py'
                }
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
