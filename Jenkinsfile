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
        
        // Added deployment stage
        stage('Deploy') {
            steps {
                script {
                    // Checks if the branch name is 'main'
                    if (env.BRANCH_NAME == 'main') {
                        echo 'Deploying to production'
                    } else {
                        echo 'Deploying to UAT'
                    }
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
