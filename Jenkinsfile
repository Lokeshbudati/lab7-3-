pipeline {
    agent any
    
    stages {
        stage('Checkout Source Code') {
            steps {
                
                checkout scm
            }
        }
        
        stage('Parallel Portal Verification') {
            parallel {
                stage('Frontend View Check') {
                    steps {
                        echo 'Launching Frontend UI interface testing thread...'
                        bat 'python frontend_check.py'
                    }
                }
                
                stage('Backend Database Check') {
                    steps {
                        echo 'Launching Backend Database connectivity testing thread...'
                        bat 'python backend_check.py'
                    }
                }
            }
        }
        
        stage('Execution Summary') {
            steps {
                echo 'SUCCESS: Combined Student Portal layers passed concurrency validation safely.'
            }
        }
    }
}
