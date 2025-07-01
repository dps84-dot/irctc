pipeline {
    agent any

    tools {
        maven 'Maven 3'   // Jenkins me Maven install ho to uska name yahi likhna
    }

    environment {
        SONAR_TOKEN = 'edb17a0641c0679f99477a0943f39de5bfa77760'
    }

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

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarCloud') {
                    sh '''
                        mvn sonar:sonar \
                        -Dsonar.projectKey=dharam84-kkeeyy_dharam \
                        -Dsonar.organization=dharam84-kkeeyy \
                        -Dsonar.host.url=https://sonarcloud.io \
                        -Dsonar.login=$SONAR_TOKEN
                    '''
                }
            }
        }
    }
}
