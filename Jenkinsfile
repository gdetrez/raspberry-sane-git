pipeline {
    agent { label 'scanner' }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'uname -a'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Push') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
