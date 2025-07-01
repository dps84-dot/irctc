pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/dps84-dot/irctc.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}
